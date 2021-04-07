---
type: lecture
date: 2022-01-24T10:00:00+02:00
title: Totuusarvot ja ehdolliset rakenteet
tldr: "Boolean-arvot True ja False, ehtorakenteet if, elif ja else"
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

1. Totuusarvot
1. Eri arvojen vertailu
1. Totuusarvojen käyttäminen ehdollisessa logiikassa
1. Ehtojen kääntäminen ja yhdistely

Suositeltavaa luettavaa:

* [https://www.pythoncheatsheet.org/#Flow-Control](https://www.pythoncheatsheet.org/#Flow-Control)
* [https://docs.python.org/3/tutorial/controlflow.html#if-statements](https://docs.python.org/3/tutorial/controlflow.html#if-statements)


## Totuusarvot


Pythonissa on kaksi totuusarvoa:

```python
tosi = True
epatosi = False
```

Lisäksi kaikki muut arvot voidaan esittää totuusarvoina `bool`-funktion avulla. Pääsääntöisesti kaikki nollaa vastaavat sekä tyhjät arvot ovat epätosia, kun taas muut arvot ovat tosia:

```python
>>> bool(0)
False
>>> bool(100)
True
>>> bool('')
False
>>> bool('hello')
True
>>> bool('False') # kaikki ei-tyhjät merkkijonot ovat tosia!
True
>>> bool('0')     # kaikki ei-tyhjät merkkijonot ovat tosia!
True
```

Vertailuoperaatiot ovat samat kuin muissa kielissä:

```python
1 < 2
4 > 2
1 != 2
1 == 1
```

Monista muista kielistä poiketen merkkijonojen vertailu onnistuu sekä `==` että `<` ja `>`-operaattoreilla!

```python
>>> "a" < "b"
True
>>> "teksti" == "teksti"
True
```

Totuusarvojen yhdistäminen ja negaatio toimivat `and`, `or`, `is` ja `not` -operaatioilla.


## Ehdollinen logiikka

Pythonin if-else -rakenne on hyvin samankaltainen kuin muissa kielissä:

```python
kaupunki = 'Helsinki'
vakiluku = 648_553

if vakiluku > 500_000:
    print(f'{kaupunki} on suuri kaupunki')
else:
    print(f'{kaupunki} on pieni kaupunki')
```

Muodostaessasi pitkiä ehtorakenteita, huomaa, että `else if` on Pythonissa `elif`.


<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-19-of-44-Conditional-Logic/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [19 of 44] Conditional Logic - Microsoft Channel 9 Video"></iframe>

## Demo: Ehdollinen logiikka

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-20-of-44-Demo-Conditional-Logic/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [20 of 44] Demo: Conditional Logic - Microsoft Channel 9 Video"></iframe>


## Useiden ehtojen käsittely

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-21-of-44-Handling-Multiple-Conditions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [21 of 44] Handling Multiple Conditions - Microsoft Channel 9 Video"></iframe>

## Demo: Useiden ehtojen käsittely

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-22-of-44-Demo-Multiple-Conditions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [22 of 44] Demo: Multiple Conditions - Microsoft Channel 9 Video"></iframe>


## Monimutkaisemmat ehdot

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-23-of-44-Complex-Conditions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [23 of 44] Complex Conditions - Microsoft Channel 9 Video"></iframe>

## Demo: Monimutkaisemmat ehdot

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-24-of-44-Demo-Complex-Conditions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [24 of 44] Demo: Complex Conditions - Microsoft Channel 9 Video"></iframe>


