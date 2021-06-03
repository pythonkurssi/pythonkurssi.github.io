---
type: lecture
date: 2022-02-28T10:00:00+02:00
title: Listat
tldr: "Arvojen lisääminen, poistaminen ja hakeminen listoita."
thumbnail: 
__links__:
    - url: https://python-s20.mooc.fi/osa-4/3-listat
      name: Python mooc
---


Tällä viikolla tutustumme Pythonin kenties yleisimpään kokoelmaan: listoihin. Listat ovat tietorakenteita, joiden pituus kasvaa joustavasti, kun niihin lisätään uusia arvoja. Listoihin voidaan lisätä arvoja myös aiempien arvojen väliin ja listan väleistä voidaan poistaa arvoja. 

Tämän oppitunnin sivu toimii muistilappuna erilaisista listaoperaatioista, joten tarvitset aiheen syvälliseksi ymmärtämiseksi myös muuta lähdemateriaalia esimerkiksi seuraavista:

* Ohjelmoinnin perusteet (mooc.fi): [Listat](https://ohjelmointi-21.mooc.fi/osa-4/3-listat)
* Python for Everybody (py4e.com): [Lists](https://www.py4e.com/html3/08-lists)
* Python documentation (docs.python.org): [Lists](https://docs.python.org/3/tutorial/introduction.html#lists)
* Python 3 – ohjelmointiopas: [sivut 62-67](http://urn.fi/URN:ISBN:978-952-335-622-1)


**Sisällysluettelo**

<div class="js-toc"></div>


## Johdanto kokoelmiin

Seuraava video esittelee tiiviisti Pythonin kokoelmat ja käsittelee niiden eroja ja käyttötarkoituksia.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-25-of-44-Collections/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [25 of 44] Collections - Microsoft Channel 9 Video"></iframe>

Eri tietorakenteet nähdään käytännössä seuraavalla videolla:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-26-of-44-Demo-Collections/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [26 of 44] Demo: Collections - Microsoft Channel 9 Video"></iframe>


## Listaoperaatiot

Listoja käytetään joko kutsumalla listan metodeja tai käyttämällä operaattoreita, kuten `+` tai `del`. Seuraavat kappaleet käyvät läpi keskeiset listaoperaatiot, joita tarvitset käsitelläksesi arvoja listoilla.

### Listan luominen

```python
tyhja_lista = []
numerolista = [42, 3.14, -1]
kaupungit = ['Helsinki', 'Espoo', 'Vantaa']
```

### Listalle lisääminen

```python
kaupungit = ['Helsinki', 'Espoo', 'Vantaa']

# append lisää loppuun
kaupungit.append('Kauniainen')

# insert lisää tiettyyn indeksiin
kaupungit.insert(0, 'Turku')

print(kaupungit) # ['Turku', 'Helsinki', 'Espoo', 'Vantaa', 'Kauniainen']
```

```python
kaupungit = ['Helsinki', 'Espoo', 'Vantaa']

# extend lisää kerralla kaikki annetun listan arvot
kaupungit.extend(['Lahti', 'Tampere'])
```

`+`-operaatio yhdistää kaksi listaa ja muodostaa niiden perusteella kolmannen listan:

```python
kaupungit1 = ['Helsinki', 'Espoo', 'Vantaa']
kaupungit2 = ['Lahti', 'Tampere']

kaikki = kaupungit1 + kaupungit2

print(kaikki) # ['Helsinki', 'Espoo', 'Vantaa', 'Lahti', 'Tampere']
```

### Listalta hakeminen

Listan alkioiden hakeminen indeksien avulla toimii aivan kuten merkkijonojen merkkien ja osamerkkijonojen hakeminen:

```python
kaupungit = ['Helsinki', 'Espoo', 'Vantaa']

kaupungit[0]    # 'Helsinki'

kaupungit[0:2]  # ['Helsinki', 'Espoo']
kaupungit[-2:]  # ['Espoo', 'Vantaa']
```


### Arvon korvaaminen

`insert`- ja `append`-metodit lisäävät listalle arvoja korvaamatta siinä valmiiksi olevia arvoja. Jos sen sijaan haluat korvata tietyssä indeksissä olevan arvon uudella, voit määritellä kohdeindeksin hakasulkuihin ja asettaa uuden arvon sijoitusoperaattorilla:

```python
kaupungit = ['Helsinki', 'Espoo', 'Vantaa']

kaupungit[0] = 'Helsingfors'

print(kaupungit) # ['Helsingfors', 'Espoo', 'Vantaa']
```

### Listalta poistaminen

```python
kaupungit = ['Helsinki', 'Espoo', 'Vantaa']

# del poistaa listalta tietyn indeksin
del kaupungit[0]

print(kaupungit)  # ['Espoo', 'Vantaa']
```

### Listan sisällön tutkiminen

Kuten merkkijonojen kanssa, arvojen etsiminen listalta tapahtuu `in`-operaatiolla:

```python
'Helsinki' in kaupungit # True
```

### Listalla olevien arvojen lukumäärä

```python
kaupungit = ['Helsinki', 'Espoo', 'Vantaa']

print(len(kaupungit)) # 3
```


### Listan arvojen läpikäynti

```python
kaupungit = ['helsinki', 'espoo', 'vantaa']

for nimi in kaupungit:
    print(nimi.capitalize())
```

### Listan arvojen läpikäynti (indeksillä)

Toisinaan listan arvoja käsiteltäessä tarvitaan myös niiden indeksejä. Erityisesti tämä on tarpeen silloin, kun listalla olevia arvoja korvataan toisilla arvoilla:

```python
kaupungit = ['helsinki', 'espoo', 'vantaa']

for i in range(0, len(kaupungit)):
    kaupungit[i] = kaupungit[i].capitalize()

print(kaupungit) # ['Helsinki', 'Espoo', 'Vantaa']
```

### Listan järjestäminen

```python
kaupungit = ['Vantaa', 'Helsinki', 'Espoo']
kaupungit.sort()

print(kaupungit) # ['Espoo', 'Helsinki', 'Vantaa']
```


## Videoiden lisenssi 

Tässä oppimateriaalissa hyödynnetyt Microsoftin [Python for Beginners -videosarjan](https://channel9.msdn.com/Series/Intro-to-Python-Development/) videot on lisensoitu [Creative Commons Attribution-Noncommercial-No Derivative Works 4.0 International](https://creativecommons.org/licenses/by-nc-nd/4.0/) -lisenssillä.
