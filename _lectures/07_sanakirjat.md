---
type: lecture
date: 2022-03-07T10:00:00+02:00
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

> Lista on kätevä tietorakenne, mutta sen rajoituksena on, että alkiot ovat indekseissä 0, 1, 2, jne. Tämä hankaloittaa alkioiden etsimistä listalta: jotta löydämme tietyn alkion, on pahimmassa tapauksessa käytävä läpi koko lista.
>
> Tutustumme seuraavaksi sanakirjaan, (englanniksi dictionary) joka on listan lisäksi toinen Pythonin perustietorakenne. Sanakirjassa jokainen alkio koostuu avaimesta ja arvosta, ja voimme etsiä ja muuttaa tietoa avaimen perusteella.
>
> *[Agile Education Research -tutkimusryhmä](https://www.helsinki.fi/en/researchgroups/data-driven-education). [Sanakirja](https://ohjelmointi-21.mooc.fi/osa-5/3-dictionary). [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.fi)*


**Sisällysluettelo**

<div class="js-toc"></div>


Tämän oppitunnin sivu toimii muistilappuna erilaisista listaoperaatioista, joten tarvitset aiheen syvälliseksi ymmärtämiseksi myös muuta lähdemateriaalia esimerkiksi seuraavista lähteistä:


* Ohjelmoinnin perusteet (mooc.fi): [Sanakirja](https://ohjelmointi-21.mooc.fi/osa-5/3-dictionary)
* Python for Everybody (py4e.com): [Dictionaries](https://www.py4e.com/html3/09-dictionaries)
* Python documentation (docs.python.org): [Dictionaries](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)
* Python 3 – ohjelmointiopas: [luku 10](http://urn.fi/URN:ISBN:978-952-335-622-1)



## Sanakirjan luonti

Pythonin sanakirjarakenne muistuttaa monilla tavoilla JSON-tietorakenteita, JavaScript-kielen objekteja sekä Javan map-tietorakenteita. Ne ovat siis kokoelmia avain-arvo-pareja. Toisin kuin listoissa, arvoja ei käsitellä pelkästään numeeristen indeksien avulla, vaan voimme määritellä avaimiksi halutessamme vaikka merkkijonoja:


```python
vakiluvut = {
    'Helsinki': 648_553,
    'Espoo': 285_018,
    'Vantaa': 229_593
}

print(vakiluvut)  # {'Helsinki': 648553, 'Espoo': 285018, 'Vantaa': 229593}
```

Yllä olevassa esimerkissä sanakirjan **avaimet**  ovat merkkijonoja eli kaupunkien nimiä. Avaimina voidaan käyttää monipuolisesti eri tyyppejä, kuten merkkijonoja tai numeroita. Huomaa, että merkkijonon kirjainkoolla on tässäkin merkitystä, eli `'Helsinki'` on eri avain kuin `'helsinki'`.

Kutakin **avainta** vastaa sanakirjassa yksi **arvo**. Tässä esimerkissä arvot ovat tiettyyn kaupunkiin kuuluvia väkilukuja, eli kokonaislukuja (int). Arvoina voidaan tallentaa **mitä tahansa tyyppejä** ja sama arvo voi esiintyä sanakirjassa moneen kertaan. Monimutkaisemmissa ohjelmissa arvoina on tyypillisesti myös sisäkkäisiä sanakirjoja.

Sanakirjat luodaan usein tyhjinä, ja niihin kerätään aineistoa muista lähteistä, kuten komentoriviltä tai tiedostoista. Tyhjä sanakirja voidaan luoda Pythonissa vastaavasti tyhjien aaltosulkujen `{}` avulla:

```python
vakiluvut = {}
```


## Arvojen asettaminen

Sanakirjaan lisätään arvoja hakasulkujen `[]` avulla. Hakasulkujen sisään kirjoitetaan se **avain**, jolle uusi **arvo** halutaan asettaa.

```python
vakiluvut = {}

# 'Turku' on avain, 186_756 on arvo:
vakiluvut['Turku'] = 186_756
```

Mikäli kyseinen arvo löytyy jo valmiiksi sanakirjasta, uusi arvo korvaa vanhan arvon.


## Arvojen hakeminen

```python
vakiluvut = { 'Helsinki': 648_553, 'Espoo': 285_018, 'Vantaa': 229_593 }

# Arvon hakeminen tietyllä arvolla
hki_vakiluku = vakiluvut['Helsinki']

print(hki_vakiluku)   # 648553
```

## Olemattoman arvon hakeminen

Mikäli haet hakasulkujen avulla arvoa, jota ei löydy sanakirjasta, aiheutuu siitä `KeyError`-virhe!

```python
vakiluvut = { 'Helsinki': 648_553, 'Espoo': 285_018, 'Vantaa': 229_593 }

oulu_vakiluku = vakiluvut['Oulu'] # Virhe!
```

Normaalitapauksessa edellä esiintyvä virhe kaataa ohjelman seuraavan ilmoituksen kaltaisella virheilmoituksella:

```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'Oulu'
```

## Arvojen tarkastaminen

Edellä esiintynyt ongelma ohjelman kaatumisesta avaimen puuttuessa voidaan ratkaista monella tapaa. Yksi suoraviivainen tapa on tarkistaa `in`-operaatiolla, löytyykö kyseistä avainta sanakirjasta:


```python
vakiluvut = { 'Helsinki': 648_553, 'Espoo': 285_018, 'Vantaa': 229_593 }

if 'Oulu' in vakiluvut:
    print(vakiluvut['Oulu'])
else:
    print('Oulun väkilukua ei löytynyt')
```


## get-metodi

Hakasulkujen lisäksi sanakirjasta voidaan hakea arvoja `get`-metodilla:

```
>>> help(dict.get)
Help on method_descriptor:

get(self, key, default=None, /)
    Return the value for key if key is in the dictionary, else default.
```

Yllä on esitetty esimerkki Pythonin `help`-funktion käyttämisestä metodin dokumentaation lukemiseksi. Ohjeesta voidaan lukea, että metodille annetaan parametrina avain, sekä vapaaehtoinen oletusarvo, joka palautetaan jos avainta ei löydy sanakirjasta. Mikäli oletusarvoa ei anneta, palautuu tuloksena `None`, jos avainta ei löydy:

```python
vakiluvut = { 'Helsinki': 648_553, 'Espoo': 285_018, 'Vantaa': 229_593 }

luku = vakiluvut.get('Oulu', 0)

print(luku)   # 0
```


## Avainten ja arvojen poistaminen sanakirjasta

Avain-arvo-parit voidaan poistaa sanakirjasta `del`-operaattorilla kuten poistimme arvoja listoilta:

```python
vakiluvut = { 'Helsinki': 648_553, 'Espoo': 285_018, 'Vantaa': 229_593 }

print('Helsinki' in vakiluvut)  # True

del vakiluvut['Helsinki']

print('Helsinki' in vakiluvut)  # False
```

## Sanakirjan läpikäynti (avaimet)

Sanakirjan avaimet voidaan käydä läpi yksinkertaisella `for`-toistorakenteella:

```python
vakiluvut = { 'Helsinki': 648_553, 'Espoo': 285_018, 'Vantaa': 229_593 }

for avain in vakiluvut:
    print(avain)
```

Edellä esitetty koodi tulostaa yksi kerrallaan kaikki **avaimet**:

```
Helsinki
Espoo
Vantaa
```

## Sanakirjan läpikäynti (avaimet ja arvot)

Voimme jatkojalostaa edellä esitettyä toistorakennetta sekä avaimien että arvojen läpikäymiseksi. Käsitellessämme kutakin **avainta**, voimma käyttää sitä hakeaksemme samasta sanakirjasta sitä vastaavan **arvon**:

```python
vakiluvut = { 'Helsinki': 648_553, 'Espoo': 285_018, 'Vantaa': 229_593 }

for avain in vakiluvut:
    vakiluku = vakiluvut[avain]  # hakee vuorollaan kutakin nimeä vastaavan väkiluvun
    print(avain, vakiluku)
```

Tällä kertaa toistorakenteessa tulostetaan:

```
Helsinki 648553
Espoo 285018
Vantaa 229593
```

