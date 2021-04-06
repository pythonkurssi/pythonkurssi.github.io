---
type: lecture
date: 2022-01-31T10:00:00+02:00
title: Toistorakenteet
tldr: "While- ja for-toistorakenne. Toistosta poistuminen ja ehdot silmukoissa."
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

1. While-toistorakenne
1. For-toistorakenne
1. Toistosta poistuminen
1. ehdot silmukoissa


## Suositeltavaa luettavaa

* [https://docs.python.org/3/tutorial/controlflow.html#for-statements](https://docs.python.org/3/tutorial/controlflow.html#for-statements)

## Toistorakenteet

Pythonin `while`-toistorakenne sekä `break`- ja `continue`-komennot toimivat kuten monissa muissakin kielissä:

```python
while True:
    vastaus = input('Mikä komento lopettaa toiston? ')
    if vastaus == 'break':
        print('Oikein!')
        break
    else:
        print('Väärin...')
```

`for`-toistorakennetta puolestaan käytetään pääsääntöisesti *for-each*-tyyliseen arvojen läpikäyntiin:

```python
kaupungit = ["HELSINKI", "ESPOO", "VANTAA"]

for kaupunki in kaupungit:
    print(kaupunki.title())
```

Jos tarkoituksena on käydä läpi kokonaislukuja (vrt. `for (int i=0; i < raja; i++)`), toteutetaan se tyypillisesti arvojen läpikäyntinä `range`-funktion avulla:

```python
>>> for luku in range(5, 10):
...     print(luku)
... 
5
6
7
8
9
```
