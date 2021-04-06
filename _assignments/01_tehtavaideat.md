---
type: assignment
date: 2022-01-17T10:00:00+02:00
title: 'Harjoitusten luonnokset'
_pdf: /static_files/assignments/asg.pdf
_attachment: /static_files/assignments/asg.zip
_solutions: /static_files/assignments/asg_solutions.pdf
due_event: 
    type: due
    date: 2022-05-23T10:00:00+03:00
    description: 'Tehtävien DL'
---



# Mikrokontrolleriosuutta tukevat perustehtävät

## Battery Charge Time Calculator

* http://www.csgnetwork.com/batterychgcalc.html

## Ohjelmat Ohmin lain soveltamiseksi: `U = R * I`

* sopivan vastuksen laskeminen?
* ledit rinnakkain + vastus?

## Ohjelma sähköisen tehon laskemiseksi: `P = U * I`

## Laitteen akun keston arviointi, kun tiedetään kapasiteetti ja keskimääräinen kulutus

* opetellaan eri SI-määreitä, kuten mikroamppeerit, milliamppeerit jne.
* bonus: virransäästötila viimeiset 20 %
* ESP32 deep sleep -virrankulutus

# Aritmetiikka ja funktiot

## Tiedoston koon ilmoittaminen muodossa TB, GB, MB, tai KB tiedoston koosta riippuen.Katso esim: [https://stackoverflow.com/a/2104107](https://stackoverflow.com/a/2104107)

## Käyttöjärjestelmän esittämän levytilan vertailu valmistajan ilmoittamaan

* 1GB = 1024 MB vs. 1GiB = 1000 MiB. Katso esim: [https://superuser.com/a/530](https://superuser.com/a/530)


## Tiedoston latausajan laskuri, kun tiedetään nettiyhteyden nopeus



## Skumppalaskuri

* Tuttu javakurssilta.



# Merkkijonot

## Käyttäjätunnusten generointi

* Chuck Norris => `cnorris` tms.

## Meiliosoitteen varmistaminen: vertaillaan case-insensitiivisesti

## IP-osoitteiden tai MAC-osoitteiden käsittely 

* selvitetään, onko annettu IP IPV4- vai IPV6-muodossa
* selvitetään, onko IP validi
* selvitetään, onko IP julkinen vai ei

## ROT13-tehtävä

* https://en.wikipedia.org/wiki/Substitution_cipher
* ![ROT13](https://upload.wikimedia.org/wikipedia/commons/2/2a/ROT13.png)

    By en:User:Matt Crypto - created with Dia, Public Domain, [https://commons.wikimedia.org/w/index.php?curid=387892](https://commons.wikimedia.org/w/index.php?curid=387892)

## Numeronyymit

* i18n
* l10n
* k8s

# Toistorakenteet

## Satunnaisen salasanan generointi

* toistorakenne
* merkkijonot

# Tiedostot

## fileinput-tekstinkäsittely (csv?)

* Muodostetaan useita käyttäjätunnuksia (hyödynnä merkkijonot-tehtävää)
* Tiedoston sisällön tulostaminen rivinumeroiden kera, vrt. `cat --number foo.txt`
* Kotus-sanalista (yhteiset sanat?)

## Tiedostojen siirtäminen päivämäärien mukaisiin alihakemistoihin

* katso esim: [https://stackoverflow.com/questions/2104080/how-can-i-check-file-size-in-python](https://stackoverflow.com/questions/2104080/how-can-i-check-file-size-in-python) ja [https://stackoverflow.com/a/8858026](https://stackoverflow.com/a/8858026).

# Listat + satunnaisuus

## Lottonumeroiden generointi

## Lottonumeroiden tarkistaminen

# Sanakirjat ja JSON

## Nimitilasto-tehtävä 

* [Digi- ja väestötietoviraston aineisto](https://www.avoindata.fi/data/fi/dataset/none)

## Postinumerot-tehtävä (Javakurssilta)

## Postitoimipaikka-tehtävä (Javakurssilta)


# Päivämäärät

## Eräpäivän laskeminen laskulle

## Juhannuksen päivämäärän selvittäminen

## Eri juhlapyhien selvittäminen tiettynä vuonna

# Haastavammat

## Tiedoston tiivisteen laskeminen

## Tekstitiedoston pakkaaminen



# MicroPython

[https://micropython-workshop.readthedocs.io/en/latest/](https://micropython-workshop.readthedocs.io/en/latest/)

## Blink

## Wifi signal detector

Skripti, joka skannaa tietyin väliajoin WIFI-verkkoja ja vilkuttaa lediä vastaanottamansa vahvimman signaalin mukaan! Esim. 90 % signaalilla: 100 ms poissa, 900 ms päällä ja 30 % signaalilla 700 ms poissa päältä ja 300 ms päällä. Vaihtoehtona piippaus signaalin vahvuuden mukaan? Ohjelman ei tarvitse liittyä WIFI-verkkoon eikä asetuksiin tarvitse määritellä tiettyä verkkoa, vaan voidaan aina olettaa mitattavan vahvinta verkkoa.

## Peruutustutka

* etäisyyssensori
* buzzer

## Reaktioaika-peli

## Led-noppa

## Liiketunnistin / murtohälytin

* Lähettää esim. mqtt-viestin tai Telegram-viestin

## Ritari ässän ledivilkku

## Nopeustesti-peli

[https://www.coinline.fi/nopeustesti-peli/](https://www.coinline.fi/nopeustesti-peli/)
