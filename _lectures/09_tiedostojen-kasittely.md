---
type: lecture
date: 2022-03-28T10:00:00+03:00
title: Tiedostojen käsittely
tldr: "Tiedostojen lukeminen ja kirjoittaminen ohjelmallisesti."
thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---

> Usein kohtaamme tilanteen, jossa haluamme tallentaa muuttujien arvot koneelle myöhempää käyttöä varten, jotta ohjelman ja koneen voi sammuttaa välillä. Tällöin voisimme lukea muuttujien arvot suoraan koneelta ilman, että joudumme joka kerta aloittamaan ohjelman kirjoittamalla muuttujien tiedot koneelle. Tällaisten tilanteiden varalta Python tukee tiedostoihin kirjoittamista sekä niistä lukemista, joista puhumme tässä luvussa.
>
> Python käsittelee tiedostoja hyvin maanläheisellä ja yksinkertaisella tavalla. Avattu tiedosto on käytännössä Pythonin tulkille pitkä merkkijono, jota ohjelma voi käsitellä halutulla tavalla. Tähän liittyy kuitenkin tärkeä varoitus: Python-tulkki ei erota järjestelmäkriittisiä tiedostoja tavallisista tekstitiedostoista! Availe ja muuttele ainoastaan sellaisia tiedostoja, joista olet varma, että niitä voi ja saa muutella.
>
> *Vanhala, E., Nikula, U. (2020). [Python 3 – ohjelmointiopas versio 1.2.1](http://urn.fi/URN:ISBN:978-952-335-622-1). LUT-yliopisto. [CC BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/)*



**Sisällysluettelo**

<div class="js-toc"></div>


## Suositeltavaa luettavaa

* Ohjelmoinnin perusteet (mooc.fi): [Datan käsittely](https://ohjelmointi-21.mooc.fi/osa-7/4-datan-kasittely)
* Python for Everybody (py4e.com): [Files](https://www.py4e.com/html3/07-files)
* Python 3 – ohjelmointiopas: [luku 6](http://urn.fi/URN:ISBN:978-952-335-622-1)

