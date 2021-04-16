---
type: lecture
date: 2022-03-28T10:00:00+03:00
title: HTTP ja JSON
tldr: "JSON-muotoisen datan lukeminen ja kirjoittaminen, HTTP-pyynnöt."
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

1. JSON-muotoisen datan lukeminen
1. JSON-datan kirjoittaminen
1. HTTP-pyynnöt

## Suositeltavaa luettavaa

* [PY4E: Networked Programs](https://www.py4e.com/html3/12-network)
* [PY4E: Using Web Services](https://www.py4e.com/html3/13-web)

## Postinumeroaineisto

GitHubista löytyy valmis projekti [https://github.com/theikkila/postinumerot](https://github.com/theikkila/postinumerot), jonka avulla voidaan hakea Postin tietokannasta kaikki postinumerotiedot. Projektissa on myös mukana valmiiksi koostettuja JSON-tiedostoja postinumeroista. 

Tässä tehtävässä sinun tulee käyttää postinumerotiedostoa [postcode_map_light.json](https://raw.githubusercontent.com/theikkila/postinumerot/master/postcode_map_light.json), joka sisältää JSON-olion, jossa postinumerot ovat avaimia ja postitoimipaikat arvoja, esimerkiksi:

```json
{
    "74701": "KIURUVESI",
    "35540": "JUUPAJOKI",
    "74700": "KIURUVESI",
    "73460": "MUURUVESI"
}
```

JSON-muotoisen merkkijonon parsiminen Pythonin tietorakenteiksi onnistuu standardikirjaston `json`-kirjastolla: [https://docs.python.org/3/library/json.html](https://docs.python.org/3/library/json.html):

```python
>>> import json
>>>
>>> json.loads("""{
...     "74701": "KIURUVESI",
...     "35540": "JUUPAJOKI",
...     "74700": "KIURUVESI",
...     "73460": "MUURUVESI"
... }""")
{'74701': 'KIURUVESI', '35540': 'JUUPAJOKI', '74700': 'KIURUVESI', '73460': 'MUURUVESI'}
>>>
```

> *"Data on postin ja sitä koskee kaikki [http://www.posti.fi/liitteet-yrityksille/ehdot/postinumeropalvelut-palvelukuvaus-ja-kayttoehdot.pdf](http://www.posti.fi/liitteet-yrityksille/ehdot/postinumeropalvelut-palvelukuvaus-ja-kayttoehdot.pdf) dokumentin käyttöehdot."*
>
> *"JSON-muunnokset ovat vapaasti käytettävissä ja muunneltavissa."*
>
> Lähde: [https://github.com/theikkila/postinumerot](https://github.com/theikkila/postinumerot)

## Tehtävän arviointi

Hyväksyttyyn suoritukseen sinun ei tarvitse toteuttaa kumpaakaan tehtävää täydellisesti. Palauta siis ohjelmat siinä kunnossa mihin saat ne toteutettua. Arviointi skaalataan suuntaa-antavasti siten, että ensimmäisen tehtävän ratkaisulla saat arvosanan 3 ja **molemmat tehtävät** ratkaisemalla arvosanan 5.


## Osa 1 (arvosanatavoite 3)

Kirjoita Python-kielinen ohjelma `postitoimipaikka.py`, joka kysyy  käyttäjältä postinumeron ja kertoo, mihin postitoimipaikkaan kyseinen postinumero kuuluu. 

Tehtävän ratkaisemiseksi sinun tulee kysyä käyttäjältä syötettä ja etsiä postinumeroaineistosta syötettä vastaava arvo. Voit joko tallentaa postinumeroaineiston koneellesi ja [lukea sen levyltä](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files) tai toteuttaa ohjelmasi [lukemaan tiedoston suoraan verkosta](https://docs.python.org/3/howto/urllib2.html).

Esimerkkisuoritus:

    $ python3 postitoimipaikka.py
    
    Kirjoita postinumero: 00100
    HELSINKI

## Osa 2 (arvosanatavoite 5)

Kirjoita Python-kielinen ohjelma `postinumerot.py`, joka kysyy käyttäjältä postitoimipaikan nimen, ja listaa kaikki kyseisen postitoimipaikan postinumerot.

Tehtävän voi ratkaista useilla tavoilla, joten käytä hetki ongelman pohtimiseen ennen kuin ryhdyt koodaamaan. Olisiko esimerkiksi helpompaa jäsentää postinumeroaineisto etukäteen uudenlaiseksi tietorakenteeksi, vai käydä avain-arvo-pareja läpi yksi kerrallaan postinumeroiden löytämiseksi. Seuraavalla viikolla käsittelemme hieman lähemmin tietorakenteiden ja algoritmien suunnittelua ja tehokkuutta.

Esimerkkisuoritus:

    $ python3 postinumerot.py

    Kirjoita postitoimipaikka: Porvoo
    Postinumerot: 06100, 06401, 06151, 06150, 06101, 06500, 06450, 06400, 06200

Yritä toteuttaa ohjelma siten, että syötetyn postitoimipaikan kirjainkoolla ei ole merkitystä. Huolehdi myös siitä, että tuntemattoman nimen syöttäminen ei kaada ohjelmaa.


## Lähteitä

Pythonin dict-tietorakenne, eli sanakirja, muistuttaa Javan map-tietorakennetta. Tulet tarvitsemaan sanakirjaa tausta-aineiston käsittelemisessä: [https://docs.python.org/3/tutorial/datastructures.html#dictionaries](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)

Tiedoston lataaminen verkosta onnistuu esim Python 3: standardikirjastoon kuuluvalla `urllib`-kirjastolla: [https://docs.python.org/3/howto/urllib2.html](https://docs.python.org/3/howto/urllib2.html).

JSON-muotoisen merkkijonon parsiminen Pythonin listoiksi, sanakirjoiksi ja muiksi tietorakenteiksi onnistuu standardikirjaston `json`-kirjastolla: [https://docs.python.org/3/library/json.html](https://docs.python.org/3/library/json.html).

