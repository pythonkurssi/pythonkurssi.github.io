---
type: assignment
date: 2022-01-17T10:00:10+02:00
title: 'MicroPython'
_pdf: /static_files/assignments/asg.pdf
_attachment: /static_files/assignments/asg.zip
_solutions: /static_files/assignments/asg_solutions.pdf
due_event: 
    type: due
    date: 2022-05-23T10:00:09+03:00
    description: 'Tehtävien DL'
---



## MicroPython

[https://micropython-workshop.readthedocs.io/en/latest/](https://micropython-workshop.readthedocs.io/en/latest/)

* Blink

    Mikrokontrollerien "hello world" -vastine.

    Oppimistavoitteet:

    * Koodin siirtäminen mikrokontrolleriin
    * Koodin suorittaminen mikrokontrollerilla
    * Ledin ja vastuksen liittäminen
    * Yksittäisen GPIO-ulostulon kontrollointi

* Liikennevalot

    Ledien kontrolloiminen ajastetusti.

    Oppimistavoitteet:

    * Ledien tilan muuttaminen GPIO-väylien avulla
    * Tapahtumien ajastaminen


* "Ritari ässän" ledivilkku

    Ideana samanlainen kuin liikennevalot, mutta valojen syttymisen ja sammuttamisen järjestys toteutettuna monipuolisemmin tekstitiedoston avulla:

    ```
    1 0 0 0 0
    0 1 0 0 0
    0 0 1 0 0
    0 0 0 1 0
    0 0 0 0 1
    0 0 0 1 0
    0 0 1 0 0
    0 1 0 0 0
    ```

    Tekstitiedostossa 1 vastaa samuutettua lediä ja 1 päällä olevaa ledia.

    Oppimistavoitteet:

    * Valojen sekvenssin lukeminen tiedostosta
    * Merkkijonomuotoisen syötteen hyödyntäminen IO-ulostulojen ohjauksessa

* Led-noppa

    Useaan led-valoon perustuva noppa, joka käynnistyy painikkeesta, ja vilkuttaa valoja satunnaisesti. 

    Oppimistavoitteet:

    * GPIO-väylän hydyntäminen painikkeen kytkemiseksi
    * Painikkeeseen reagointi 

* Reaktioaika-peli

* Peruutustutka

    Oppimistavoitteet:

    * Etäisyyssensorin kytkennät ja analogisten lukemien käsittely
    * Buzzer-summerin kytkennät ja hyödyntäminen
    * Ohjelmalogiikan, eli piippausten pituuden, toteuttaminen mittalaitteen tulosten perusteella

* Wifi signal detector

    Skripti, joka skannaa tietyin väliajoin WIFI-verkkoja ja vilkuttaa lediä vastaanottamansa vahvimman signaalin mukaan! Esim. 90 % signaalilla: 100 ms poissa, 900 ms päällä ja 30 % signaalilla 700 ms poissa päältä ja 300 ms päällä. Vaihtoehtona piippaus signaalin vahvuuden mukaan? Ohjelman ei tarvitse liittyä WIFI-verkkoon eikä asetuksiin tarvitse määritellä tiettyä verkkoa, vaan voidaan aina olettaa mitattavan vahvinta verkkoa.

    Oppimistavoitteet:

    * ESP32:n WiFi-verkkojen skannaus
    * Vahvimman signaalin löytäminen listalta
    * Ohjelmalogiikan toteuttaminen saadun signaalivahvuuden perusteella

* Kukkaruukun kastelumuistutin

    Telegram-viestin lähettäminen mullan kosteuden laskettua alle raja-arvon. 

    Oppimistavoitteet:

    * Deep sleep
    * Soil moisture sensor
    * Telegram


* Itsenäinen web-pohjainen murtohälytin (haastava)

    Hälytin, joka lähettää Telegram-viestin havaittuaan liikettä.

    Oppimistavoitteet:

    * Liiketunnistimen kytkentä ja liikkeeseen reagointi
    * Telegram-viestin lähettäminen REST-apin avulla
    * Deep sleep -tilan hyödyntäminen, josta herääminen toteutetaan liiketunnistimen avulla



* Nopeustesti-peli

    Katso [https://www.coinline.fi/nopeustesti-peli/](https://www.coinline.fi/nopeustesti-peli/)
