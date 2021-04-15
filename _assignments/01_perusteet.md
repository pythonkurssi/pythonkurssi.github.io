---
type: assignment
date: 2022-01-17T10:00:01+02:00
title: 'Ohjelmoinnin aloitus'
_pdf: /static_files/assignments/asg.pdf
_attachment: /static_files/assignments/asg.zip
_solutions: /static_files/assignments/asg_solutions.pdf
due_event: 
    type: due
    date: 2022-05-23T10:00:00+03:00
    description: 'Tehtävien DL'
---



## Mikrokontrolleriosuutta tukevat perustehtävät

* Battery Charge Time Calculator

    http://www.csgnetwork.com/batterychgcalc.html

* Ohjelmat Ohmin lain soveltamiseksi: `U = R * I`

    * sopivan vastuksen laskeminen?
    * ledit rinnakkain + vastus?

* Lämpötila Fahrenheitista Celsiukseksi

    * Monet sensorit, kuten ESP32-mikrokontrollerin sisäänrakennettu lämpömittari, ilmoittavat lämpötilan Fahrenheit-yksikössä:

        ```
        > import esp32
        > esp32.raw_temperature()
        124
        ```

        Kirjoita ohjelma, joka muuttaa esimerkiksi yllä esitetyn lämpötilan 124 Fahrenheitia Celsius-asteiksi (51.1 &deg;C). Muunnoskaavan löydät esimerkiksi osoitteesta [https://www.laskurini.fi/hyoty/yksikkomuuntimet/lampotilamuunnin](https://www.laskurini.fi/hyoty/yksikkomuuntimet/lampotilamuunnin).


* Ohjelma sähköisen tehon laskemiseksi: `P = U * I`

* Laitteen akun keston arviointi, kun tiedetään kapasiteetti ja keskimääräinen kulutus

    * ESP32 deep sleep -virrankulutus
    * opetellaan eri SI-määreitä, kuten mikroamppeerit, milliamppeerit jne.
    * läppärin virransäästötilan vaikutukset akunkestoon (display off, sleep...)
    * bonus: virransäästötila viimeiset 20 %
