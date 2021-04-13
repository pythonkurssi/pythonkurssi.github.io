---
type: lecture
date: 2022-04-18T10:00:00+03:00
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

Sensorien ja ohjattavien laitteiden kytkeminen sekä niiden hyödyntäminen ohjelmallisesti.

Reagoiminen painikkeisiin.

Sensorit
Piirit
Sensorit ja toimilaitteet (ultraääni, valo, ääni, kosketus, servo, DC-moottori)


## Electric Current: Crash Course Physics

<iframe width="560" height="315" src="https://www.youtube.com/embed/HXOok3mfMLM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

YouTube: [ESP32 Tutorial using MicroPython - Let's Get Started!](https://www.youtube.com/watch?v=QopRAwUP5ds)


## Pinnien kytkennät

Laitteen pinnit: [https://randomnerdtutorials.com/esp32-cam-ai-thinker-pinout/](https://randomnerdtutorials.com/esp32-cam-ai-thinker-pinout/)

Arduinon esimerkki *LEDCSoftwareFade* toimii, kun muuttaa siitä piirilevyn LED-pinnin id:ksi 4:

```c++
#define LED_PIN            4
```


## Tutoriaali

Freenove-tutoriaali: [https://github.com/Freenove/Freenove_Ultimate_Starter_Kit/blob/master/Tutorial.pdf](https://github.com/Freenove/Freenove_Ultimate_Starter_Kit/blob/master/Tutorial.pdf)

## Lämpötilasensorin käyttäminen

[Using a Temperature Sensor with Micropython running on an Adafruit Feather Huzzah ESP8266](https://pythonforundergradengineers.com/micropython-temp-sensor.html)