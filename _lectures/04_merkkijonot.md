---
type: lecture
date: 2022-02-07T10:00:00+02:00
title: Merkkijonot
tldr: "Merkkijonojen käsittely, vertailu ja osamerkkijonot"
thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---

Merkkijonon pituus, osajonot, metodit


* [PY4E: Strings](https://www.py4e.com/lessons/strings)



## Merkkijonot

Pythonin merkkijonoissa voidaan käyttää joko heittomerkkejä `'` tai lainausmerkkejä `"`. Moniriviset merkkijonot aloitetaan ja päätetään kolmella merkillä. Merkkijonojen yhdistämiseen voidaan käyttää `+` -merkkiä:

```python
kaupunki = 'Helsinki'
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




## Formatting Strings

Python 3:ssa merkkijonojen yhdistelemiseksi on myös plus-merkkiä kätevämpi tapa, eli [formatted string literals](https://docs.python.org/3/tutorial/inputoutput.html#formatted-string-literals):

```python
kaupunki = 'Helsinki'
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