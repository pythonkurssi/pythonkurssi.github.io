---
type: lecture
date: 2022-03-14T10:00:00+02:00
title: Ajan käsittely ja satunnaisuus
tldr: "Pythonin aikakirjaston käyttäminen ja satunnaisuus ohjelmissa."
thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---


Tällä oppitunnilla perehdymme Pythonin tapohin käsitellä aikaa. Aikaa voidaan käsitellä esimerkiksi `datetime`-moduulin avulla, mihin perehdymmekin tällä tunnilla.

Ajan käsittelyn lisäksi tutustumme siihen, miten voimme luoda ohjelmia, jotka hyödyntävät satunnaisuutta logiikassaan.

**Sisällysluettelo**

<div class="js-toc"></div>


**Suositeltavaa luettavaa**

* Ohjelmoinnin perusteet (mooc.fi): [Aikojen käsittely](https://ohjelmointi-21.mooc.fi/osa-7/3-aikojen-kasittely)
* Ohjelmoinnin perusteet (mooc.fi): [Satunnaisuus](https://ohjelmointi-21.mooc.fi/osa-7/2-satunnaisuus)
* Python documentation (docs.python.org): [datetime - Basic date and time types](https://docs.python.org/3/library/datetime.html)
* Python documentation (docs.python.org): [random - Generate pseudo-random numbers](https://docs.python.org/3/library/random.html)
* Python 3 – ohjelmointiopas: [sivut 79-82](http://urn.fi/URN:ISBN:978-952-335-622-1)




## Aikamoduulin käyttäminen omassa koodissa

Seuraava video käsittelee Pythonin `datetime`-modullin käyttöönottoa omassa koodissamme. Opit lisäämään tai vähentämään päiviä tietystä päivämäärästä, sekä muotoilemaan ajankohdat eri maissa käytettyjen päivämäärämuotoilujen mukaiseksi.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-15-of-44-Date-Data-Types/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [15 of 44] Date Data Types - Microsoft Channel 9 Video"></iframe>

```python
from datetime import datetime, timedelta

nykyhetki = datetime.now()

print('Nykyinen kellonaika on ' + str(nykyhetki))

viikko = timedelta(days=7)

print('Viikon päästä on ' + str(nykyhetki + viikko))
```

Koodiesimerkit käsitellään käytännön tasolla seuraavassa videossa:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-16-of-44-Demo-Dates/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [16 of 44] Demo: Dates - Microsoft Channel 9 Video"></iframe>


## Tuntitehtävä: ikälaskuri

Kirjoita ohjelma, joka pyytää käyttäjältä päivämäärän muodossa `pp.kk.vvvv`, ja kertoo kuinka pitkä aika kuluvan päivän ja annetun päivän välillä on.


## Tuntitehtävä: pyhäpäivälaskuri

Kirjoitetaan ohjelma, joka selvittää juhannuksen sekä muut ajankohdaltaan vaihtelevat juhlapyhät annettuna vuonna. Toteutetaan ohjelma siten, että muodostettu aineisto voidaan tuoda Google Calendar -sovellukseen import-toiminnolla.

* [Suomen juhlapäivät (Wikipedia)](https://fi.wikipedia.org/wiki/Suomen_juhlap%C3%A4iv%C3%A4t)
* [Pääsiäisen laskeminen (Wikipedia)](https://fi.wikipedia.org/wiki/P%C3%A4%C3%A4si%C3%A4isen_laskeminen)



## Virheet ohjelmissa (errors, runtime errors, exceptions...)

Aikaisemmassa videossa huomasimme, miten virheellisessä muodossa syötetty päivämäärä kaatoi koko ohjelman, kun sitä yritettiin muuttaa `datetime`-olioksi `strptime`-metodilla. Virheelliset syötteet ja erilaiset yllättävät virhetilanteet aiheuttavat ohjelmissa tyypillisesti **poikkeuksia**, joihin voidaan varautua etukäteen. Seuraavat videot käsittelevät **poikkeustenhallintaa**, jolla voimme jo etukäteen varautua virhetilanteisiin kirjoittamalla virheitä käsitteleviä koodilohkoja.

Seuraava video esittelee erilaisiin virheisiin liittyvät termit ja käsitteet sekä poikkeusten käsittelyyn liittyvän syntaksin:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-17-of-44-Error-Handling/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [17 of 44] Error Handling - Microsoft Channel 9 Video"></iframe>

Poikkeustenkäsittelyä esitellään käytännön tasolla seuraavalla videolla:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-18-of-44-Demo-Error-Handling/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [18 of 44] Demo: Error Handling - Microsoft Channel 9 Video"></iframe>



## Videoiden lisenssi 

Tässä oppimateriaalissa hyödynnetyt Microsoftin [Python for Beginners -videosarjan](https://channel9.msdn.com/Series/Intro-to-Python-Development/) videot on lisensoitu [Creative Commons Attribution-Noncommercial-No Derivative Works 4.0 International](https://creativecommons.org/licenses/by-nc-nd/4.0/) -lisenssillä.
