---
type: lecture
date: 2022-02-14T10:00:00+02:00
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

**Sisällysluettelo**

Olemme käyttäneet tällä ohjelmointikurssilla aikaisempien aiheiden yhteydessä lukuisia valmiita funktioita, kuten `input`, `round`, `floor`, `ceil`, `range` ja `print`. Funktiot ovat olleet luonteva osa ongelmanratkaisua, vaikka emme ole toistaiseksi kiinnittäneet niihin suurta huomiota tai toteuttaneet omia funktioita.

Tällä kertaa perehdymme tarkemmin omien funktioiden toteuttamiseen ja kutsumiseen sekä siihen, miten voimme välittää arvoja funktioille ja takaisin.

Syitä oman ohjelman jakamiseksi useisiin funktioihin on lukuisia. Ensinnäkin niiden avulla voidaan vähentää toisteisuutta, jos samoja operaatioita tehdään useita kertoja tai useissa eri kohdissa koodia. Toiseksi funktioiden avulla voidaan vähentää kompleksisuutta, eli pilkkoa iso monimutkainen kokonaisuus pienemmiksi, helpommin ymmärrettäviksi paloiksi. 


<div class="js-toc"></div>


**Suositeltavaa luettavaa**

* Ohjelmoinnin perusteet (mooc.fi): [Omat funktiot](https://ohjelmointi-21.mooc.fi/osa-3/4-omat-funktiot)
* Python for Everybody (py4e.com): [Functions](https://www.py4e.com/html3/04-functions)
* Python documentation (docs.python.org): [Defining functions](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)
* Python 3 – ohjelmointiopas: [luku 5](http://urn.fi/URN:ISBN:978-952-335-622-1)


## Johdatus funktioihin

Seuraavalla videolla esitellään funktioiden kirjoittamisen hyötyjä sekä funktioihin liittyvää käsitteistöä:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-29-of-44-Introducing-Functions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [29 of 44] Introducing Functions - Microsoft Channel 9 Video"></iframe>

Edellä esitetyn videon teoria laitetaan käytäntöön tällä videolla, jolla näet funktioiden konkreettisen toteutuksen VS Code -editorissa:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-30-of-44-Demo-Functions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [30 of 44] Demo: Functions - Microsoft Channel 9 Video"></iframe>




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





## Funktion parametrit

Seuraa video esittelee parametrien määrittelemistä funktioille, sekä parametrien oletusarvoja.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-31-of-44-Parameterized-functions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [31 of 44] Parameterized functions - Microsoft Channel 9 Video"></iframe>

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-32-of-44-Demo-Parameterized-Functions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [32 of 44] Demo: Parameterized Functions - Microsoft Channel 9 Video"></iframe>



## Parametrin välittäminen funktiolle

Palataan edellisellä viikolla esitettyyn esimerkkiin, jossa tietyn otsikon jälkeen tulostettiin otsikon pituuden verran `=`-merkkejä tulostetun otsikon korostamiseksi:

```python
otsikko = 'Parametrin välittäminen funktiolle'

print(otsikko)
print('=' * len(otsikko))
```

Jos oletamme, että ohjelmassamme eri kohdissa tulostaa otsikoita, ei tätä koodia kannata kopioida, vaan se kannattaa toteuttaa funktioksi. Toteuttaminen funktiona helpottaa koodin luettavuutta, koska funktion nimi kertoo sen toiminnasta ilman teknisiä yksityiskohtia:

```python
tulosta_otsikko('Parametrin välittäminen funktiolle')
```

Funktio myös parantaa ylläpidettävyyttä, koska mahdolliset tulevat muutokset täytyy tehdä ainoastaan yhteen paikkaan koodissa.

`tulosta_otsikko`-funktiomme otsikossa, sulkujen sisällä, on määriteltävä se parametrimuuttuja, johon funktiolle annettava merkkijono asetataan. Tämä muuttuja on voimassa ainoastaan funktion sisällä ja se vaihtelee jokaisella suorituskerralla funktiokutsussa välitetyn merkkijonon mukaan:

```python
def tulosta_otsikko(otsikko):
    print(otsikko)
    print('=' * len(otsikko))
```

Tätä funktiota voidaan nyt kutsua eri puolilta koodia eri arvoilla, ja se tulostaa sille annetut tekstit sekä tekstiin liittyvän korostuksen:

```python
tulosta_otsikko('Johdatus funktioihin')

print() # Tyhjä rivi otsikoiden väliin

tulosta_otsikko('Parametrin välittäminen funktiolle')
```

```
Johdatus funktioihin
====================

Parametrin välittäminen funktiolle
==================================
```


## Pythonin moduulit ja paketit

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-33-of-44-Modules-and-packages/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [33 of 44] Modules and packages - Microsoft Channel 9 Video"></iframe>


## Ulkoisen moduulin hyödyntäminen: random

Oletetaan seuraavaksi, että haluamme luoda satunnaisia salasanoja generoivan Python-ohjelman. Tämän ohjelman apuna voimme käyttää Pythonin valmista `random`-moduulia:

```python
import random
```

Random-moduulista löytyy meille erityisen hyödyllinen funktio, `random.choice`, joka palauttaa sille annetusta merkkijonosta yhden satunnaisen merkin. Kutsumalla tätä funktiota toistuvasti saamme muodostettua lopulta haluamamme pituisen satunnaisen salasanan:

```python
import random

pienet_kirjaimet = 'abcdefghijklmnopqrstuvwxyzåäö'
isot_kirjaimet = pienet_kirjaimet.upper()
numerot = '0123456789'
erikoismerkit = '<>,;.:-!\"#¤$%&/\\()[]'

def anna_satunnainen_merkki():
    merkit = pienet_kirjaimet + isot_kirjaimet + numerot + erikoismerkit
    return random.choice(merkit)  # palauttaa yhden satunnaisen merkin

def generoi_salasana(pituus=20):
    salasana = ''

    while len(salasana) < pituus:
        salasana += anna_satunnainen_merkki()
    
    return salasana

print(f'Salasana 1: {generoi_salasana()}')
print(f'Salasana 2: {generoi_salasana()}')

print(f'Vahva salasana: {generoi_salasana(128)}')
```

Tässä esimerkissä salasanan generointi funktiossa on erityisen hyödyllistä, koska voimme nyt generoida lukuisia salasanoja ilman että joudumme toistamaan koodia. Voimme myös parametrin avulla määritellä generoitavan salasanan pituuden.


## Exra: Virtual Environments

Mikäli kehität käyttöjärjestelmälläsi useita erillisiä Python-projekteja, voi niiden ristiriitaisista riippuvuuksista syntyä ongelmia. Seuraavat videot käsittelevät Pythonin virtuaalisia ympäristöjä, jotka mahdollistavat Python-projektisi eristämisen muista projekteista siten, että jokainen projekti asentaa riippuvuudet yhteisen hakemiston sijasta omaan virtuaaliseen ympäristöönsä.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-34-of-44-Virtual-Environments/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [34 of 44] Virtual Environments - Microsoft Channel 9 Video"></iframe>

Videon ohjeesta poiketen sinun ei tarvitse asentaa `venv`-pakettia erikseen, koska se tulee valmiiksi mukana nykyisissä Python-versioissa.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-35-of-44-Demo-Virtual-environments-packages/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [35 of 44] Demo: Virtual environments packages - Microsoft Channel 9 Video"></iframe>




## Videoiden lisenssi 

Tässä oppimateriaalissa hyödynnetyt Microsoftin [Python for Beginners -videosarjan](https://channel9.msdn.com/Series/Intro-to-Python-Development/) videot on lisensoitu [Creative Commons Attribution-Noncommercial-No Derivative Works 4.0 International](https://creativecommons.org/licenses/by-nc-nd/4.0/) -lisenssillä.
