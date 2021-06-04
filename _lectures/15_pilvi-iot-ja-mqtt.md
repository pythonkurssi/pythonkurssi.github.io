---
type: lecture
date: 2022-05-09T10:00:00+03:00
title: Pilvi-IoT ja MQTT-protokolla
tldr: "MQTT-viestien lähettäminen ja vastaanottaminen pilvipalvelun kanssa"

thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---



**Sisällysluettelo**

<div class="js-toc"></div>

## ESP32 MicroPython MQTT Tutorial with Raspberry Pi, DHT-22 & OLED

<iframe width="560" height="315" src="https://www.youtube.com/embed/_vcQTyLU1WY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Sensorien lukemien lähettäminen MQTT-viestien avulla

Lämpötila-, kosteus- ja kaasusensorin tietojen välittäminen MQTT-palvelimelle MicroPythonilla: [https://github.com/pythonkurssi/environmental-development-board](https://github.com/pythonkurssi/environmental-development-board)


## Liitäntöjen ohjaaminen vastaanotettujen viestien avulla

[https://pypi.org/project/micropython-umqtt.simple/](https://pypi.org/project/micropython-umqtt.simple/)

## How mqtt works?

* publisher, subscriber and broker
* topics and messages
* Quality of Service (0, 1, 2)
* HTTP vs. MQTT


## Kurssin aiheiden soveltaminen IoT-projektissa

**Aihe-ehdotukset:**

* Pysäköintitutka
* WiFi-skanneri
* Reaktiopeli
* Langaton hälytinjärjestelmä
