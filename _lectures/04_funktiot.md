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


# Funktiot Pythonin dokumentaatiossa

[https://docs.python.org/3/tutorial/controlflow.html#defining-functions](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)

# Funktiot

Pythonin funktiot muistuttavat hyvin suuresti esimerkiksi JavaScriptin funktioita. Parametrien ja paluuarvojen välitys tapahtuu samalla tavoin, ainoastaan syntaksissa on pieniä eroja:

```python
def laske_summa(lista_numeroista):
    summa = 0
    for n in lista_numeroista:
        summa += n
    return summa
```

Pythonista löytyy **paljon** perusoperaatioita myös valmiina, eli oman `laske_summa`-funktion sijaan voimme kutsua Pythonin valmista `sum`-funktiota.


