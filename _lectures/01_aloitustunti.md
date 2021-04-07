---
type: lecture
date: 2022-01-17T10:00:00+02:00
title: Aloitustunti
tldr: "Kurssin yleiset järjestelyt, työkalut ja ohjelmoinnin aloitus"
thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---

# Python-ohjelmoinnin aloitus

Oppitunnilla käytämme aluksi Pythonia komentoriviltä interaktiivisella tulkilla, jotta opimme nopeasti kokeilemisen kautta käyttämään Pythonin perusrakenteita. Tämän jälkeen tutustumme Python-tiedostojen editointiin VS Codella.

Lopuksi tutustumme myös muihin tapoihin hyödyntää Pythonia: "Python as a swiss army knife".

Oppitunnin aiheet:

1. Kurssin järjestelmät ja työkalut
1. Python-koodin suorittaminen ja tulkin käyttäminen
1. VSCode-editori
1. Muuttujat
1. Merkkijonot ja numerotyypit


## Python as a calculator: Read–eval–print loop (REPL)

> *"Python can be used as a calculator to compute arithmetic operations like addition, subtraction, multiplication and division. Python can also be used for trigonometric calculations and statistical calculations."*
>
> *Peter D. Kazarinoff. Problem Solving with Python. [Python as a Calculator.](https://problemsolvingwithpython.com/03-The-Python-REPL/03.01-Python-as-a-Calculator/)*


Pythonia voidaan käyttää komentoriviltä interaktiivisen tulkin avulla. Se onkin helpoin tapa tutustua kielen ominaisuuksiin. Python käynnistyy oletuksena interaktiivisessa tilassa komennolla `python3`, tai asennuksestasi riippuen esim. `python` tai `py`.

```
$ python3
Python 3.8.5 (default, Jul 28 2020, 12:59:40)
[GCC 9.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.

>>> 1 + 2 + 3
6
```

Interaktiivisella tulkilla lausekkeiden tuloksia ei tarvitse erikseen tulostaa, vaan sijoittamattomat arvot näytetään automaattisesit ruudulla.

Kokeile Pythonin laskuoperaatioita sivun [https://www.pythoncheatsheet.org/#Python-Basics](https://www.pythoncheatsheet.org/#Python-Basics) ohjeiden mukaan!




## Introducing Python

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-2-of-44-Introducing-Python/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [2 of 44] Introducing Python - Microsoft Channel 9 Video"></iframe>

[https://docs.microsoft.com/en-us/learn/modules/intro-to-python/2-what-is-python](https://docs.microsoft.com/en-us/learn/modules/intro-to-python/2-what-is-python)


## Getting started

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-3-of-44-Getting-Started/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [3 of 44] Getting Started - Microsoft Channel 9 Video"></iframe>

## Configuring Visual Studio Code

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-4-of-44-Configuring-Visual-Studio-Code/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [4 of 44] Configuring Visual Studio Code - Microsoft Channel 9 Video"></iframe>

[https://marketplace.visualstudio.com/items?itemName=ms-python.python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)



## Tulostaminen

Tulostaminen tapahtuu `print`-funktiolla, jolle voidaan antaa tarvittaessa useampia tulostettavia arvoja:

```python
>>> print('Hello world!')
>>> print('Hello', 'world!')
```

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-5-of-44-Using-Print/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [5 of 44] Using Print - Microsoft Channel 9 Video"></iframe>


## Demo: Hello, World

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-6-of-44-Demo-Hello-World/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [6 of 44] Demo: Hello, World - Microsoft Channel 9 Video"></iframe>



## Syötteiden lukeminen

```python
>>> nimi = input('Mikä on nimesi? ')
```



## Kommentit

Pythonissa yksiriviset kommentit alkavat `#`-merkillä:

```python
# tämä on yksirivinen kommentti
```

Yksirivisiä kommentteja voidaan kätevästi kirjoittaa myös koodirivin loppuun. Mikäli tarvitset pidempiä kommentteja, ne voidaan kirjoittaa kolmen lainausmerkin sisään:

```python
""" tämä on monirivinen merkkijono, joita
    käytetään pythonissa myös usein kommentteina """
```

Toisin kuin monissa muissa kielissä, Pythonissa kauttaviivalla ei voida aloittaa kommenttia:

```
// tämä ei ole kommentti!

/* tämäkään ei ole kommentti */
```

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-7-of-44-Comments/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [7 of 44] Comments - Microsoft Channel 9 Video"></iframe>

## Demo: Comments

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-8-of-44-Demo-Comments/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [8 of 44] Demo: Comments - Microsoft Channel 9 Video"></iframe>

## Muuttujat ja tietotyypit

```python
kaupunki = "Helsinki"
vakiluku = 648_553

type(kaupunki) # str
type(vakiluku) # int
```


## Merkkijonot

Pythonin merkkijonoissa voidaan käyttää joko heittomerkkejä `'` tai lainausmerkkejä `"`. Moniriviset merkkijonot aloitetaan ja päätetään kolmella merkillä. Merkkijonojen yhdistämiseen voidaan käyttää `+` -merkkiä:

```python
kaupunki = "Helsinki"
vakiluku = 648_553

print('Kaupungissa ' + kaupunki + ' on ' + str(vakiluku) + ' asukasta!')
```

Yllä oleva koodi tulostaa seuraavan rivin:

```
Kaupungissa Helsinki on 648553 asukasta!
```

Huomaa, että Pythonissa `+`-operaatiolla merkkijonoihin voidaan yhdistää ainoastaan toisia merkkijonoja. Mikäli yrittäisimme yhdistää numeromuotoisen väkiluvun suoraan sitä edeltävän merkkijonon perään, saisimme seuraavan virheen:

```
TypeError: can only concatenate str (not "int") to str
```

Tämän ongelman kiertämiseksi edellisessä esimerkissä väkiluku on ensin muutettu merkkijonoksi (string): `str(vakiluku)`.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-9-of-44-String-Concepts/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [9 of 44] String Concepts - Microsoft Channel 9 Video"></iframe>

## Demo: Strings

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-10-of-44-Demo-Strings/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [10 of 44] Demo: Strings - Microsoft Channel 9 Video"></iframe>

## Formatting Strings

Python 3:ssa merkkijonojen yhdistelemiseksi on myös plus-merkkiä kätevämpi tapa, eli [formatted string literals](https://docs.python.org/3/tutorial/inputoutput.html#formatted-string-literals):

```python
kaupunki = "Helsinki"
vakiluku = 648_553
print(f'Kaupungissa {kaupunki} on {vakiluku} asukasta!')
```

```
Kaupungissa Helsinki on 648553 asukasta!
```

Yllä muotoiluja sisältävän merkkijonon eteen on laitettu f-kirjain ja merkkijonoon sijoitettavat arvot on kirjoitettu aaltosulkujen sisään:

```python
muotoiltu = f'merkkijono {muuttuja}'
```


<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-11-of-44-Formatting-Strings/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [11 of 44] Formatting Strings - Microsoft Channel 9 Video"></iframe>

## Demo: Formatting Strings

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-12-of-44-Demo-Formatting-Strings/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [12 of 44] Demo: Formatting Strings - Microsoft Channel 9 Video"></iframe>

## Merkkijonojen käsittely

Pythonissa merkkijonojen merkkejä ja osamerkkijonoja voidaan hakea indeksien avulla. Yksi numero tarkoittaa yksittäistä merkkiä, kun taas `i:j` tarkoittaa väliä. Jos alku- tai loppuindeksi jätetään ilmoittamatta, käytetään alkuna nollaa ja loppuna merkkijonon viimeistä merkkiä. Python sallii myös negatiiviset indeksit, jotka lasketaan merkkijonon lopusta lähtien!

```python
kaupunki = 'Helsinki'
kaupunki[0]     # 'H'
kaupunki[0:2]   # 'He'
kaupunki[2:4]   # 'ls'
kaupunki[-1]    # 'i'
kaupunki[-2:]   # 'ki'
```

Tavallisten `upper` ja `lower` -metodien lisäksi Pythonin merkkijonoilla on kätevä `title`-metodi:

```python
kaupunki = 'vantaa'
kaupunki.upper() # 'VANTAA'
kaupunki.lower() # 'vantaa'
kaupunki.title() # 'Vantaa'
```

Merkkijonojen sisältämiä osamerkkijonoja voidaan selvittää `in`-operaation avulla:

```python
'java' in 'javascript'  # True
'ham' in 'hamster'      # True
```


## Lukujen tyyppimuunnokset ja pyöristäminen

Merkkijonoja voidaan muuttaa eri lukutyypeiksi, ja lukutyyppejä voidaan muuttaa toisiksi `int`- ja `float`-funktioilla:

```python
kymmenen = int('10')

ika = int(input('Kerro ikäsi: '))
```

```python
pii = float('3.14')

hinta = float(input('Syötä pizzan hinta: '))
```

Pyöristäminen onnistuu `round`-funktiolla, jolle voidaan myös kertoa, kuinka monen desimaalin tarkkuudella pyöristys halutaan tehdä:

```python
>>> round(3.14)
3
>>> round(3.14, 1)
3.1
```

Luvut voidaan muuttaa merkkijonoiksi `str`-funktiolla:

```python
>>> hinta = 9.90
>>> print("Hinta: " + str(hinta))
Hinta: 9.9
```

Sama koodi ei toimisi ilman `str`-muunnosta, koska Python ei salli katenoida lukuja sekä merkkijonoja:

```python
>>> hinta = 9.90
>>> print("Hinta: " + hinta)

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "float") to str
```


<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-13-of-44-Numeric-Data-Types/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [13 of 44] Numeric Data Types - Microsoft Channel 9 Video"></iframe>

## Demo: Numbers

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-14-of-44-Demo-Numbers/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [14 of 44] Demo: Numbers - Microsoft Channel 9 Video"></iframe>




## import-käsky

Pythonissa sekä kielen standardikirjaston moduulit että omat ja `pip`-komennolla asennetut moduulit voidaan ottaa käyttöön `import`-käskyllä:

```python
>>> import math
>>> math.pi
3.141592653589793
>>> round(math.pi, 5)
3.14159
>>> math.floor(math.pi)
3
>>> math.ceil(math.pi)
4
```

Yksittäisiä funktioita, arvoja tai luokkia voidaan ottaa käyttöön syntaksilla `from moduuli import asia`:

```python
>>> from math import log2
>>> log2(50_000)
15.609640474436812
```

**Bonus**: Kokeile myös seuraavia:

```python
import __hello__
import antigravity
import this
```




## Valikoituja hyödyllisiä komentoja

**help** -funktio näyttää ohjeita sille annetun arvon tai funktion käyttämiseksi:

    >>> help(print)
    Help on built-in function print in module builtins:

    print(...)
        print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)

        Prints the values to a stream, or to sys.stdout by default.
        Optional keyword arguments:
        file:  a file-like object (stream); defaults to the current sys.stdout.
        sep:   string inserted between values, default a space.
        end:   string appended after the last value, default a newline.
        flush: whether to forcibly flush the stream.

**type** -funktio kertoo sille annetun arvon tyypin:

    >>> type(mysteerimuuttuja)
    <class 'list'>

**dir** -funktio kertoo moduulin sisältämät arvot, funktiot ja luokat:

    >>> import math
    >>> dir(math)
    ['__doc__', '__loader__', '__name__', '__package__', 
    '__spec__', 'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 
    'atanh', 'ceil', 'comb', 'copysign', 'cos', 'cosh', 'degrees', 
    'dist', 'e', 'erf', 'erfc', 'exp', 'expm1', 'fabs', 
    'factorial', 'floor', 'fmod', 'frexp', 'fsum', 'gamma', 'gcd',
    'hypot', 'inf', 'isclose', 'isfinite', 'isinf', 'isnan', 
    'isqrt', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'log2', 
    'modf', 'nan', 'perm', 'pi', 'pow', 'prod', 'radians', 
    'remainder', 'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'tau', 
    'trunc']

