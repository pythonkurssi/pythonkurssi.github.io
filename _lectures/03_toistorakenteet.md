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

* [PY4E: Loops and Iterations](https://www.py4e.com/lessons/loops)
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

## Loops

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-27-of-44-Loops/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [27 of 44] Loops - Microsoft Channel 9 Video"></iframe>

## Demo: Loops

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-28-of-44-Demo-Loops/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [28 of 44] Demo: Loops - Microsoft Channel 9 Video"></iframe>




---

Microsoftin [Python for Beginners -videosarjan](https://channel9.msdn.com/Series/Intro-to-Python-Development/) videot on lisensoitu [Creative Commons Attribution-Noncommercial-No Derivative Works 4.0 International](https://creativecommons.org/licenses/by-nc-nd/4.0/) -lisenssillä.