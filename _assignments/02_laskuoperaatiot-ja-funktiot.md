---
type: assignment
date: 2022-01-17T10:00:02+02:00
title: 'Laskuoperaatiot ja funktiot'
_pdf: /static_files/assignments/asg.pdf
_attachment: /static_files/assignments/asg.zip
_solutions: /static_files/assignments/asg_solutions.pdf
due_event: 
    type: due
    date: 2022-05-23T10:00:01+03:00
    description: 'Tehtävien DL'
---



## Laskuoperaatiot ja funktiot

* Tiedoston koon ilmoittaminen muodossa TB, GB, MB, tai KB tiedoston koosta riippuen

    Katso esim: [https://stackoverflow.com/a/2104107](https://stackoverflow.com/a/2104107)

* Käyttöjärjestelmän esittämän levytilan vertailu valmistajan ilmoittamaan

    * 1GB = 1024 MB vs. 1GiB = 1000 MiB. 

        Katso esim: [https://superuser.com/a/530](https://superuser.com/a/530)

        ```
        >>> import esp
        >>>
        >>> esp.flash_size()
        4194304
        ```

        Mikä on ESP32:n flash-muistin koko megatavuina, kun tavuina se on yllä esitetty 4&nbsp;194&nbsp;304 tavua?


* Tiedoston latausajan laskuri, kun tiedetään nettiyhteyden nopeus ja tiedoston koko

    * käsitteet tavu ja bitti: muutos biteistä tavuiksi
    * muutokset sekunneista tunneiksi, minuuteiksi ja sekunneiksi
    * bonus: huomioidaan HTTP-protokollan overhead?


* Skumppalaskuri

    Tuttu javakurssilta.
