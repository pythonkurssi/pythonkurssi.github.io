---
type: lecture
date: 2022-04-25T10:00:00+03:00
title: Mikrokontrollerin liitännät
tldr: "Sensorien ja ohjattavien laitteiden kytkeminen sekä niiden hyödyntäminen ohjelmallisesti."
thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---

Tämän oppitunnin aikana perehdymme sensorien ja ohjattavien laitteiden kytkemiseen sekä niiden hyödyntämiseen ohjelmallisesti.


**Sisällysluettelo**

<div class="js-toc"></div>


<!--* Reagoiminen painikkeisiin
* Sensorit ja toimilaitteet
  * lämpötila
  * ultraääni
  * valo
  * ääni
  * kosketus
  * servo
  * DC-moottori)-->

## Esimerkkiprojekti

Oppitunnilla perehdytään etäisyyttä, lämpötilaa, kosteutta ja liikettä mittaavaan esimerkkiprojektiin, joka löytyy osoitteesta [https://github.com/pythonkurssi/esp32-sensor-demo](https://github.com/pythonkurssi/esp32-sensor-demo).

<!-- ## Digitaaliset syötteet -->

<!-- TODO: digitaalisen signaalin lukeminen -->

<!-- TODO: pull-up- ja pull-down-vastukset -->

<!-- ## Painikkeeseen reagointi -->

<!-- TODO: Digitaalisen pinnin alustaminen -->

<!-- TODO: Arvon lukeminen ja arvojen heilahteluun varautuminen -->


## Analogiset syötteet

Analogisten sensorien, kuten lämpötilasensorin arvon lukeminen poikkeaa merkittävästi painikkeen tilan lukemisesta. Kun painikkeen arvo voi olla ainoastaan 0 tai 1, lämpötilasensorin arvo voi olla mitä tahansa ennalta määritellyltä väliltä.

### Lämpötilan mittaaminen

Analogisten arvojen mittaaminen perustuu niiden läpi päästämän jännitteen mittaamiseen. Esimerkiksi LM35DZ-lämpötilasensorin ulostulojännite 0 &deg;C lämpötilassa on 0 V ja se kasvaa aina 10 mV (0.001 V) jokaista lämpöastetta kohden. Tarkemmat tiedot sensorin toiminnasta löydät sen [datasheetistä](https://www.ti.com/lit/ds/symlink/lm35.pdf).

> *"On the ESP32 ADC functionality is available on Pins 32-39. Note that, when using the default configuration, input voltages on the ADC pin must be between 0.0v and 1.0v (anything above 1.0v will just read as 4095). Attenuation must be applied in order to increase this usable voltage range."*
>
> MicroPython, 2021. [Quick reference for the ESP32
](https://docs.micropython.org/en/latest/esp32/quickref.html#adc-analog-to-digital-conversion)

Yllä olevan otteen mukaisesti ESP32-mikrokontrollerin väylät 32-39 kykenevät muuntamaan analogisen signaalin digitaaliseksi. Oletuksena väylät lukevat korkeintaan 1 voltin jännitteitä, mutta asteikkoa voidaan tarvittaessa muuttaa ohjelmallisesti.

[Analogisen signaalin lukemiseksi MicroPythonilla](https://docs.micropython.org/en/latest/esp32/quickref.html#adc-analog-to-digital-conversion) tarvitsemme ADC- ja PIN-luokkia:

```python
from machine import ADC
from machine import Pin

adc = ADC(Pin(32))
adc.read() # esim. 687
```

Tässä esimerkissä luetun arvon `687` tulkitsemiseksi tarvitsemme tiedon siitä, miten luettu jännite on skaalattu ja mikä siinä käytettävä asteikko on. 

[MicroPythonin dokumentaation](https://docs.micropython.org/en/latest/esp32/quickref.html#adc-analog-to-digital-conversion) mukaan jännite luetaan oletuksena väliltä 0-1 V ja se ilmoitetaan oletuksena 12 bittisenä lukuna, eli väliltä 0-4095. 

Käytännössä tämä tarkoittaa sitä, että luettu luku 0 vastaa 0 volttia ja luku 4095 vastaa yhtä volttia. Saamamme luku 687 vastaa siis:

```python
lukema = adc.read() # esim. 687

jannite_mv = lukema / 4_095 * 1_000 # jännite muutettuna mV (167.76556776556777)
```

Koska LM35DZ-sensorin ulostulossa 10 mV vastaa yhtä lämpöastetta, saadaan millivontteina ilmoitettu jännite muutettua asteiksi jakamalla se kymmenellä:

```python
lampotila = jannite_mv / 10 # noin 16.78 °C
```

Vastaavalla logiikalla voidaan lukea myös muita analogisia signaaleja. Viimeisessä vaiheessa analogisesta syötteestä luettu jännite tulee vain muuttaa eri yksiköihin kunkin sensorin toimintalogiikan mukaisesti.

*Tässä esimerkissä on sovellettu tutoriaaleja [MicroPython: DS18B20 Temperature Sensor with ESP32 and ESP8266](https://randomnerdtutorials.com/micropython-ds18b20-esp32-esp8266/) sekä [Guide for LM35, LM335 and LM34 Temperature Sensors with Arduino](https://randomnerdtutorials.com/arduino-lm35-lm335-lm34-temperature-sensor/).*


### Mittavirheiden välttäminen

Jos mittaat esimerkiksi lämpötilan useita kertoja peräkkäin, huomaat, että lukema vaihtelee melkoisesti eri mittauskertojen välillä. Yksittäisissä mittauksissa esiintyvien mittausvirheiden välttämiseksi kannattaa usein tehdä useita mittauksia ja käyttää ohjelmassa esimerkiksi mittausten keskiarvoa tai juoksevaa keskiarvoa:

```python
# yksi tulos, iso virhe
mittaustulos = adc.read()

# kymmenen tulosta, joissa yksittäisen virheen merkitys vähenee
kymmenen_mittaustulosta = [ adc.read() for x in range(0, 10) ]
```

Listalle kerättyjen mittaustulosten keskiarvo voidaan laskea yksinkertaisesti esimerkiksi seuraavalla funktiolla:

```python
def keskiarvo(tulokset):
    return sum(tulokset) / len(tulokset)
```

## Analogisen signaalin vaimentaminen

Lämpötilasensorin kohdalla mittaväli nollasta yhteen volttiin riittää normaalin huoneenlämmön mittaamiseen. Jännitteen nousu yli yhden voltin johtaa kuitenkin aina samaan tulokseen, eli maksimiarvoon 4095. Mikäli oletuksena käytettävä jänniteväli ei riitä, joudutaan signaalia vaimentamaan.

[MicroPythonin koodiesimerkin](https://docs.micropython.org/en/latest/esp32/quickref.html#adc-analog-to-digital-conversion) mukaisesti vaimennus voidaan tehdä esimerkiksi 11dB:n tasolla, jolloin sama mitta-asteikko 0 - 4095 vastaakin jänniteväliä 0 V - 3.6 V:

```python
adc.atten(ADC.ATTN_11DB)  # set 11dB input attenuation (voltage range roughly 0.0v - 3.6v)

lukema = adc.read()       # esim. 2277
jannite_mv = lukema / 4_095 * 3_600

jannite_mv                # 2002 mV => 2 V
```

Signaalin vaimennuksen avulla voimme käyttää esimerkiksi valovastusta (photoresistor) mitataksemme eri tilojen valaistusta: [Reading a photoresistor on ESP32 with MicroPython](https://blog.gypsyengineer.com/en/diy-electronics/reading-photoresistor-on-esp32-with-micropython.html).

Huomaa, että ESP32:n GPIO-väylien sallitun jännitteen yläraja on 3,6 V ja suuremmat jännitteet rikkovat laitteesi.


## Electric Current: Crash Course Physics

<iframe width="560" height="315" src="https://www.youtube.com/embed/HXOok3mfMLM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

YouTube: [ESP32 Tutorial using MicroPython - Let's Get Started!](https://www.youtube.com/watch?v=QopRAwUP5ds)


## Pinnien kytkennät

Laitteen pinnit: [https://randomnerdtutorials.com/esp32-cam-ai-thinker-pinout/](https://randomnerdtutorials.com/esp32-cam-ai-thinker-pinout/)

Arduinon esimerkki *LEDCSoftwareFade* toimii, kun muuttaa siitä piirilevyn LED-pinnin id:ksi 4:

```c++
#define LED_PIN            4
```

## Lisämateriaalit

**Tutoriaali**

Freenove-tutoriaali: [https://github.com/Freenove/Freenove_Ultimate_Starter_Kit/blob/master/Tutorial.pdf](https://github.com/Freenove/Freenove_Ultimate_Starter_Kit/blob/master/Tutorial.pdf)


**Lämpötilasensorin käyttäminen**

[Using a Temperature Sensor with Micropython running on an Adafruit Feather Huzzah ESP8266](https://pythonforundergradengineers.com/micropython-temp-sensor.html)