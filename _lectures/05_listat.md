---
type: lecture
date: 2022-02-14T10:00:00+02:00
title: Listat
tldr: "Arvojen lisääminen, poistaminen ja hakeminen listoita."
thumbnail: 
__links__:
    - url: https://python-s20.mooc.fi/osa-4/3-listat
      name: Python mooc
---

Oppitunnin aiheet:

1. Arvojen lisääminen, poistaminen ja hakeminen listoita
1. Listojen läpikäynti
1. Listan osien käsittely

# Suositeltavaa luettavaa

* [PY4E: Lists](https://www.py4e.com/html3/08-lists)
* [Listat Pythonin dokumentaatiossa](https://docs.python.org/3/tutorial/introduction.html#lists)



## Collections

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-25-of-44-Collections/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [25 of 44] Collections - Microsoft Channel 9 Video"></iframe>

## Demo: Collections

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-26-of-44-Demo-Collections/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [26 of 44] Demo: Collections - Microsoft Channel 9 Video"></iframe>



# Listan luominen ja arvojen lisääminen

Listan luominen, arvojen lisääminen, poistaminen sekä listojen yhdistäminen:

```python
kaupungit = ["Helsinki", "Espoo", "Vantaa"]

# append lisää loppuun
kaupungit.append("Kauniainen")

# insert lisää annettuun indeksiin
kaupungit.insert(0, "Turku")

# del poistaa listalta
del kaupungit[0]

# extend lisää annetun listan arvot
kaupungit.extend(["Lahti", "Tampere"])

# + yhdistää, mutta ei muuta alkuperäistä listaa
yhdistetty = kaupungit + ["Oulu", "Rovaniemi"]
```

Listan arvojen hakeminen toimii täsmälleen kuten merkkijonojen tapauksessa:

```python
>>> kaupungit[0]    # Yksittäinen arvo
'Turku'
>>> kaupungit[0:2]  # Arvot väliltä [0, 2[
['Turku', 'Helsinki']
>>> kaupungit[-2:]  # Arvot lopusta alkaen toiseksi viimeisestä
['Lahti', 'Tampere']
```

Arvojen etsiminen listalta tapahtuu `in`-operaatiolla:

```python
"Helsinki" in kaupungit # True
```

Listoille on lisäksi erilaisia operaatioita, kuten järjestäminen:

```python
kaupungit = ['Vantaa', 'Helsinki', 'Espoo']
kaupungit.sort()
kaupungit # ['Espoo', 'Helsinki', 'Vantaa']
```

**Edistynyt esimerkki:** erilaisia listoja voidaan luoda kätevästi "list comprehension"-syntaksilla:

```python
isolla = [k.upper() for k in kaupungit]
isolla # ['HELSINKI', 'ESPOO', 'VANTAA']
```

### Monikot (tuple)

Listojen lisäksi pythonissa on kiinteäpituuksinen kokoelma **monikko**, eli **tuple**:

```python
monikko = ('monta', 'arvoa')
```

Monikkoja, kuten listoja, voidaan purkaa kätevästi muuttujiin sijoitusoperaatiolla:

```python
numerot = (1, 2, 3, 4)

yksi, kaksi, kolme, nelja = numerot
```

Monikoita käytetään "pellin alla" monissa tilanteissa, kuten esimerkiksi sanakirjarakenteen avain-arvo-parien läpikäynnissä.

---

Microsoftin [Python for Beginners -videosarjan](https://channel9.msdn.com/Series/Intro-to-Python-Development/) videot on lisensoitu [Creative Commons Attribution-Noncommercial-No Derivative Works 4.0 International](https://creativecommons.org/licenses/by-nc-nd/4.0/) -lisenssillä.