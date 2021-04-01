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
