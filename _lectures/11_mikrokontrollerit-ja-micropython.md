---
type: lecture
date: 2022-04-11T10:00:00+03:00
title: Mikrokontrollerit ja MicroPython
tldr: "MicroPythonin asentaminen ESP32-mikrokontrolleriin."
thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---

Oppitunnin aiheet:

1. MicroPythonin asentaminen ESP32-mikrokontrolleriin.
1. Koodin siirtäminen mikrokontrolleriin Pymakr-työkalulla.
1. MicroPytonin standardikirjaston käyttäminen
1. Lämpötilasensorin lukeminen
1. Ledin vilkuttaminen

## Arduino IDE:n käyttöönotto (draft, ESP32 CAM)

Arduino IDE:n asennus Windows storen kautta: [https://www.microsoft.com/fi-fi/p/arduino-ide/9nblggh4rsd8](https://www.microsoft.com/fi-fi/p/arduino-ide/9nblggh4rsd8)

Yhdistäminen: [https://randomnerdtutorials.com/program-upload-code-esp32-cam/](https://randomnerdtutorials.com/program-upload-code-esp32-cam/)

Arduino IDE:n käyttöönotto:
[https://randomnerdtutorials.com/installing-the-esp32-board-in-arduino-ide-windows-instructions/](https://randomnerdtutorials.com/installing-the-esp32-board-in-arduino-ide-windows-instructions/)

Asetustiedoston osoite: 

```
https://dl.espressif.com/dl/package_esp32_index.json
```

Lähdekoodien korjaus (compilation terminated -virhe) [https://forum.arduino.cc/index.php?topic=577858.0](https://forum.arduino.cc/index.php?topic=577858.0)

## Pinnien kytkennät

Laitteen pinnit: [https://randomnerdtutorials.com/esp32-cam-ai-thinker-pinout/](https://randomnerdtutorials.com/esp32-cam-ai-thinker-pinout/)

Arduinon esimerkki *LEDCSoftwareFade* toimii, kun muuttaa siitä piirilevyn LED-pinnin id:ksi 4:

```c++
#define LED_PIN            4
```

## MicroPythonin asentaminen

Heikki Hietalan erinomaiset oppaat ja esimerkit:

1. [https://www.sabulo.com/sb/arduino/moving-on-from-arduino-to-esp32-part1/](https://www.sabulo.com/sb/arduino/moving-on-from-arduino-to-esp32-part1/)
1. [http://www.sabulo.com/sb/arduino/moving-on-from-arduino-to-esp32-part-2-micropython/](http://www.sabulo.com/sb/arduino/moving-on-from-arduino-to-esp32-part-2-micropython/)
1. [https://www.sabulo.com/sb/arduino/moving-on-from-arduino-to-esp32-part-3-upycraft-and-blink/](https://www.sabulo.com/sb/arduino/moving-on-from-arduino-to-esp32-part-3-upycraft-and-blink/)

## Esptool-työkalun asennus

```
py -m pip install --upgrade pip --user
pip install esptool
```

ESP32 CAM -laitteella firmwareasennus tulee tehdä IO0-pinnin ollessa kytkettynä maahan. Asennuksen jälkeen IO0 pitää irrottaa.

Firmwaren lataus: [https://micropython.org/download/esp32/](https://micropython.org/download/esp32/). Tallenna itsellesi firmware-tiedosto, joka on muodossa `esp32-idf4-vvvvkkpp-vX.YZ.bin`.

Tarkista järjestelmäsi asetuksista ESP32:n käyttämän COM-portin numero (ohje). Tämän jälkeen voit asentaa firmwaren komentorivillä seuraavilla komennoilla:

### erase_flash

```
> python32 -m esptool --chip esp32 --port COM3 erase_flash

esptool.py v3.0
Serial port COM3
Connecting....
Chip is ESP32-D0WDQ6 (revision 1)
Features: WiFi, BT, Dual Core, 240MHz, VRef calibration in efuse, Coding Scheme None
Crystal is 40MHz
MAC: 24:6f:28:15:45:24
Uploading stub...
Running stub...
Stub running...
Erasing flash (this may take a while)...
Chip erase completed successfully in 7.1s
Hard resetting via RTS pin...
```

### write_flash

```
> python -m esptool --chip esp32 --port COM3 --baud 460800 write_flash -z 0x1000 `esp32-idf4-vvvvkkpp-vX.YZ.bin

esptool.py v3.0
Serial port COM3
Connecting........_____.....__
Chip is ESP32-D0WDQ6 (revision 1)
Features: WiFi, BT, Dual Core, 240MHz, VRef calibration in efuse, Coding Scheme None
Crystal is 40MHz
MAC: 24:6f:28:15:45:24
Uploading stub...
Running stub...
Stub running...
Changing baud rate to 460800
Changed.
Configuring flash size...
Compressed 1484624 bytes to 951640...
Wrote 1484624 bytes (951640 compressed) at 0x00001000 in 21.8 seconds (effective 546.0 kbit/s)...
Hash of data verified.

Leaving...
Hard resetting via RTS pin...
```

### Putty-yhteyden testaus

Katso edeltä sabulo.com-ohje tekstiyhteyden muodostamiseksi Putty-sovelluksella. 

```
ets Jun  8 2016 00:22:57

rst:0x1 (POWERON_RESET),boot:0x13 (SPI_FAST_FLASH_BOOT)
configsip: 0, SPIWP:0xee
clk_drv:0x00,q_drv:0x00,d_drv:0x00,cs0_drv:0x00,hd_drv:0x00,wp_drv:0x00
mode:DIO, clock div:2
load:0x3fff0018,len:4
load:0x3fff001c,len:5148
load:0x40078000,len:12880
load:0x40080400,len:3484
entry 0x40080630
MicroPython v1.14 on 2021-02-02; ESP32 module with ESP32
Type "help()" for more information.
>>>
```

### Ohjelmien siirtäminen mikrokontrolleriin

MicroPython-ohjelmat voidaan siirtää tietokoneelta mikrokontrolleriin useilla eri työkaluilla. Tällä kurssilla hyödynnämme VS Code:a ja [Pycom](https://pycom.io/):in kehittämää Pymakr-laajennosta.

Pymakr-laajennuksen käyttöohjeet löytyvät osoitteesta [https://docs.pycom.io/gettingstarted/software/vscode/](https://docs.pycom.io/gettingstarted/software/vscode/).

Laajennus voidaan asentaa VS Coden sovelluskaupasta: [https://marketplace.visualstudio.com/items?itemName=pycom.Pymakr](https://marketplace.visualstudio.com/items?itemName=pycom.Pymakr).

