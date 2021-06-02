---
type: lecture
date: 2022-05-02T10:00:00+03:00
title: MicroPython ja WiFi
tldr: "Mikrokontrollerin liittäminen langattomaan lähiverkkoon."

thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---

**Tämän oppitunnin aiheita:**

* Mikrokontrollerin liittäminen langattomaan lähiverkkoon.
* Tiedoston lukeminen verkosta.
* ISO/OSI-mallin mukaiset kerrokset vs. IoT-protokollakerrokset

Protokollat:

* Bluetooth
* BLE
* ZigBee
* Z-Wave
* WiFi
* NFC
* LTE, HSPA
* 433 MHz...

## Oppitunnin esimerkkiprojektit

Telegram-viestien lähettäminen ja vastaanottaminen mikrokontrollerilla: [https://github.com/pythonkurssi/micropython-utelegram](https://github.com/pythonkurssi/micropython-utelegram)

Lämpötila-, kosteus- ja kaasusensorin tietojen välittäminen MQTT-palvelimelle MicroPythonilla: [https://github.com/pythonkurssi/environmental-development-board](https://github.com/pythonkurssi/environmental-development-board)

ESP32:n käyttäminen tukiasemana oikeaan Wifi-verkkoon yhdistämiseksi: WifiManager [https://github.com/pythonkurssi/WiFiManager](https://github.com/pythonkurssi/WiFiManager)