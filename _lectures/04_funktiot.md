---
type: lecture
date: 2022-02-07T10:00:00+02:00
title: Funktiot
tldr: "Funktioiden määrittely. Parametrit ja paluuarvot. Toisessa tiedostossa olevan funktion kutsuminen."
thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---


Oppitunnin sisältö:

1. Funktioiden määrittely
1. Funktioiden kutsuminen
1. Parametrit ja paluuarvot
1. Toisessa tiedostossa olevan funktion kutsuminen
1. Tyyppivihjeet

## Suositeltavaa luettavaa

* [PY4E: Functions](https://www.py4e.com/html3/04-functions)
* [Funktiot Pythonin dokumentaatiossa](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)

## Funktioiden määrittely

Pythonin funktiot muistuttavat hyvin suuresti esimerkiksi JavaScriptin funktioita. Parametrien ja paluuarvojen välitys tapahtuu samalla tavoin, ainoastaan syntaksissa on pieniä eroja:

```python
def laske_summa(lista_numeroista):
    summa = 0
    for n in lista_numeroista:
        summa += n
    return summa
```

Pythonista löytyy **paljon** perusoperaatioita myös valmiina, eli oman `laske_summa`-funktion sijaan voimme kutsua Pythonin valmista `sum`-funktiota.




## Introducing Functions

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-29-of-44-Introducing-Functions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [29 of 44] Introducing Functions - Microsoft Channel 9 Video"></iframe>

## Demo: Functions

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-30-of-44-Demo-Functions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [30 of 44] Demo: Functions - Microsoft Channel 9 Video"></iframe>

## Parameterized functions

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-31-of-44-Parameterized-functions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [31 of 44] Parameterized functions - Microsoft Channel 9 Video"></iframe>

## Demo: Parameterized Functions

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-32-of-44-Demo-Parameterized-Functions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [32 of 44] Demo: Parameterized Functions - Microsoft Channel 9 Video"></iframe>

## Modules and packages

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-33-of-44-Modules-and-packages/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [33 of 44] Modules and packages - Microsoft Channel 9 Video"></iframe>

## Exra: Virtual Environments

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-34-of-44-Virtual-Environments/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [34 of 44] Virtual Environments - Microsoft Channel 9 Video"></iframe>

## Demo: Virtual environments packages

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-35-of-44-Demo-Virtual-environments-packages/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [35 of 44] Demo: Virtual environments packages - Microsoft Channel 9 Video"></iframe>



---

Microsoftin [Python for Beginners -videosarjan](https://channel9.msdn.com/Series/Intro-to-Python-Development/) videot on lisensoitu [Creative Commons Attribution-Noncommercial-No Derivative Works 4.0 International](https://creativecommons.org/licenses/by-nc-nd/4.0/) -lisenssillä.