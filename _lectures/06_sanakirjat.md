---
type: lecture
date: 2022-02-28T10:00:00+02:00
title: Sanakirjat
tldr: "Arvojen käsitteleminen sanakirjan avulla avainten ja arvojen pareina."
thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
__links__:
    - url: https://python-s20.mooc.fi/osa-5/3-dictionary
      name: Python mooc
---

Tällä oppitunnilla opettelemme käsittelemään dataa avainten ja arvojen pareina.

Oppitunnin aiheet:

1. Sanakirjan luominen
1. Arvojen lisääminen sanakirjaan
1. Arvojen poistaminen sanakirjasta
1. Sanakirjan läpikäynti
1. Avainten ja arvojen etsiminen

## Suositeltavaa luettavaa

[https://docs.python.org/3/tutorial/datastructures.html#dictionaries](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)

## Sanakirjat (dict)

Pythonin sanakirjarakenne muistuttaa monilla tavoilla JSON-tietorakenteita, JavaScript-kielen objekteja sekä Javan map-tietorakenteita. Ne ovat siis kokoelmia avain-arvo-pareja:

```python
vakiluvut = {
    'Helsinki': 648553,
    'Espoo': 285018,
    'Vantaa': 229593
}
```

Arvojen hakeminen, lisääminen ja korvaaminen toimivat kuten JavaScriptissä:

```python
>>> # Arvon hakeminen:
>>> vakiluvut['Helsinki']
648553
>>> 
>>> # Arvon lisääminen:
>>> vakiluvut['Turku'] = 186_756
>>>
>>> # Arvon asettaminen (ja hakeminen):
>>> vakiluvut['Helsinki'] = vakiluvut['Helsinki'] + 1
```

Sanakirjan avaimet ja arvot omina kokoelminaan:

```python
>>> vakiluvut.keys()
dict_keys(['Helsinki', 'Espoo', 'Vantaa', 'Turku'])
>>>
>>> vakiluvut.values()
dict_values([648554, 285018, 229593, 186756])
```

Jos haluat selvittää, löytyykö tiettyä avainta tai arvoa sanakirjasta, voit käyttää `in`-operaatiota:

```python
>>> 'Helsinki' in vakiluvut
True
>>>
>>> # in tarkistaa vain avaimista:
>>> 648554 in vakiluvut
False
>>> 
>>> # voit tehdä tarkistuksen myös suoraan sanakirjan arvoihin
>>> 648554 in vakiluvut.values()
True

```

Sanakirjan avaimia ja arvoja voidaan käsitellä myös pareina (monikkoina):

```python
>>> vakiluvut.items()
dict_items([('Helsinki', 648554), ('Espoo', 285018), ('Vantaa', 229593), ('Turku', 186756)])
```

Sanakirjan avaimet voidaan käydä läpi yksinkertaisella `for`-toistorakenteella:

```python
>>> for avain in vakiluvut:
...     print(avain)
... 
Helsinki
Espoo
Vantaa
Turku
```

Jos toistossa halutaan käsitellä sekä avaimia että arvoja, kannattaa ne käydä läpi pareina (ks. yllä items() sekä monikot):

```python
>>> for nimi, luku in vakiluvut.items():
...     print(f'{nimi} ({luku})')
... 
Helsinki (648554)
Espoo (285018)
Vantaa (229593)
Turku (186756)
```

