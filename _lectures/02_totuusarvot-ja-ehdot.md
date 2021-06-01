---
type: lecture
date: 2022-01-24T10:00:00+02:00
title: Totuusarvot ja ehtolauseet
tldr: "Boolean-arvot True ja False, ehtolauseet if, elif ja else"
thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---

# Totuusarvot ja ehtolauseet


Tällä tunnilla tutustumme Pythonin totuusarvoihin `True` ja `False` sekä niihin liittyvään logiikkaan. Opimme vertailemaan eri arvoja toisiinsa ja tekemään vertailun tulosten perusteella ehdollisesti suoritettavaa ohjelmalogiikkaa.

Myöhemmin tällä kurssilla hyödynnämme totuusarvoja ja ehtoja toteuttaessamme toistorakenteita, joissa koodia toistetaan haluamiemme ehtojen mukaisesti.

**Sisällysluettelo**

<div class="js-toc"></div>

**Suositeltavaa luettavaa**

* Ohjelmoinnin perusteet (mooc.fi): [ehtorakenne](https://ohjelmointi-21.mooc.fi/osa-1/5-ehtorakenne)
* Python for Everybody (py4e.com): [Conditional execution](https://www.py4e.com/html3/03-conditional)
* Python documentation (docs.python.org): [If statements](https://docs.python.org/3/tutorial/controlflow.html#if-statements)
* Python 3 – ohjelmointiopas: [luku 3](http://urn.fi/URN:ISBN:978-952-335-622-1)

## Totuusarvot (boolean)

Pythonissa on kaksi totuusarvoa:

```python
tosi = True
epatosi = False
```

Näiden totuusarvojen tyyppi on `bool`, joka tulee sanasta **boolean**:

```
# arvon tyyppi voidaan tarkistaa Pythonin type-funktiolla:
>>> type(True)
<class 'bool'>

>>> type(False)
<class 'bool'>
```

Totuusarvoja voidaan monella tapaa käyttää kuten numeroita ja merkkijonoja. Niitä voidaan esimerkiksi tulostaa ja asettaa muuttujiin:

```python
print(True)     # True

muuttuja = True
print(muuttuja) # True
```

Totuusarvojen kääntäminen, eli negaatio, tapahtuu Pythonissa `not`-operaattorin avulla:

```python
tosi = True         # True
epatosi = not tosi  # False
```

## Vertailuoperaatiot

Totuusarvoja kirjoitetaan suhteellisen harvoin koodiin sellaisenaan. Sen sijaan totuusarvot syntyvät tyypillisesti erilaisten vertailujen tuloksena:

```python
ika = 22
print(ika >= 18)    # tulostaa True
```

Vertailujen tuloksia voidaan toki tulostaa kuten yllä, mutta ne voidaan myös asettaa talteen muuttujiin:

```python
ika = 22
taysi_ikainen = ika >= 18   # True asetetaan talteen muuttujaan
```

"Suurempi kuin" vertailun lisäksi Pythonissa on lukuisia muita vertailuoperaattoreita, joilla voimme vertailla eri arvoja toisiinsa:

Operaattori | Selitys
------------|-----------
`==`        | yhtä suuri kuin
`!=`        | eri suuruinen kuin
`>`         | suurempi kuin
`>=`	      | suurempi tai yhtä suuri kuin
`<` 	      | pienempi kuin
`<=`	      | pienempi tai yhtä suuri kuin
`and`       | ja
`or`        | tai
`not`       | käänteinen totuusarvo

Kaikki seuraavan esimerkin muuttujat saavat arvoikseen `True`, eli vertailujen tulokset ovat tosia:

```python
luku = 1

yhtasuuri = luku == 1
suurempi = luku > 0
pienempi = luku < 2
suurempi_tai_sama = luku >= 1
pienempi_tai_sama = luku <= 1
eri_suuruinen = luku != 0
```

# If-ehtolause

Totuusarvojen yleinen käyttötarkoitus on koodin suorittaminen vain tietyn ehdon täyttyessä. Tällöin tietyt koodirivit suoritetaan ainoastaan silloin, kun niille asetettu ehto toteutuu.

Tarkastettava ehto kirjoitetaan `if`-avainsanan jälkeen sulkujen sisään: `if ehto:`. Ehdon toteutuessa suoritettavat koodirivit kirjoitetaan uuteen koodilohkoon heti `if`-lauseen jälkeen. Pythonissa koodilohkot erotetaan toisistaan sisennyksillä, jotka ovat tyypillisesti neljä välilyöntiä:

```python
if ehto:
    # ehdollisesti suoritettava koodi

# ehtorakenteen jälkeen suoritus jatkuu täällä
```

Ehtona on aina oltava totuusarvo tai totuusarvon saava lauseke, esimerkiksi:

```python
ika = int(input('Kerro ikäsi: '))

taysi_ikainen = ika >= 18

if taysi_ikainen:
    # tähän lohkoon kirjoitettu koodi suoritetaan 
    # vain, jos taysi_ikainen sai arvon True
    print("Olet täysi-ikäinen")
```

If-lauseen ehtona voi olla myös lauseke, joka suoritetaan (evaluoidaan) ensin, ja päätös tehdään saadun tuloksen mukaan.

```python
if ika >= 18:
    print("Olet täysi-ikäinen")
```


## Vertailu "== True"

Toisinaan ehtolauseen sisään saatetaan kirjoittaa jonkin arvon vertailu `True`-arvoon:

```python
if taysi_ikainen == True:
    # ...
```

Tämä on kuitenkin turhaa, koska `taysi_ikainen == True` saa aina arvokseen saman arvon kuin `taysi_ikainen`. Voimme käyttää siis aina suoraan `taysi_ikainen`-muuttujan arvoa:

```python
if taysi_ikainen:
    # ...
```


## Merkkijonojen vertailu

Merkkijonojen vertailun tulokset riippuvat Pythonissa merkkijonojen kirjainkoosta. Seuraavalla videolla käsitellään ratkaisu merkkijonojen vertailemiseksi kirjainkoosta riippumatta:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-19-of-44-Conditional-Logic/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [19 of 44] Conditional Logic - Microsoft Channel 9 Video"></iframe>



## Syötteiden kysyminen ja ehtolauseet ohjelmalogiikan osana

Seuraavalla videolla esitellään ohjelmissa tyypillinen rakenne, jossa ohjelman logiikka ja tulosteet ovat aina samat, mutta ohjelmassa käytettävä veroprosentti vaihtelee hinnan mukaan ehtolauseen avulla. Videolla vertaillaan lisäksi käyttäjän syöttämää merkkijonoa kirjainkoosta riippumatta.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-20-of-44-Demo-Conditional-Logic/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [20 of 44] Demo: Conditional Logic - Microsoft Channel 9 Video"></iframe>



## Ehtojen yhdistäminen

Totuusarvoja voidaan yhdistellä ja- sekä tai-operaatioilla. Näiden operaatioiden tuloksena saadaan myös totuusarvoja.

### Ja (and)

Ehdon "a ja b" (`a and b`) arvoksi tulee `True` vain silloin, kun **molemmat puolet** ovat tosia. 

Esimerkiksi, jos kesäkuukausiksi lasketaan kesä, heinä ja elokuu, voidaan `on_kesa`-muuttujan logiikassa hyödyntää `and`-operaatiota:

```java
on_kesa = kuukausi >= 6 and kuukausi <= 8
```

Ja-operaation tulos voidaan esittää kahden arvon yhdistelmien avulla taulukkona siten, että vasemmalla olevien `a`:n ja `b`:n kaikkien arvojen yhdistelmien perusteella esitetään kyseisten arvojen ja-operaation tulos `a and b`:

| a     | b     | a and b |
|-------|-------|--------  |
| True  | True  | True     |
| True  | False | False    |
| False | True  | False    |
| False | False | False    |


### Tai (or)

Ehdon "a tai b" (`a or b`) arvoksi tulee `True` aina, kun **vähintään toinen arvoista** on `True`:

Esimerkiksi, jos talvikuukausiksi lasketaan tammi-, helmi-, marras- ja joulukuu, tarvitaan kesän logiikasta poiketen `or`-operaatiota:

```java
on_talvi = kuukausi <= 2 or kuukausi >= 11
```

Tai-operaation tulos voidaan esittää kahden arvon yhdistelmien avulla taulukkona siten, että vasemmalla olevien `a`:n ja `b`:n kaikkien arvojen yhdistelmien perusteella esitetään kyseisten arvojen tai-operaation tulos `a || b`:

| a     | b     | a or b |
|-------|-------|----------|
| True  | True  | True     |
| True  | False | True     |
| False | True  | True     |
| False | False | False    |



## Ehtorakenteet (ja)

Ehtolauseessa voidaan suorittaa (evaluoida) myös monimutkaisempia lausekkeita, joissa tehdään useita eri vertailuja:

```python
kello = 16

if kello >= 10 and kello < 18:
    # tähän lohkoon kirjoitettu koodi suoritetaan vain,
    # jos molemmat and-operaation ympärillä olevat ehdot toteutuvat
    print("Hyvää päivää!")
```

Edellä oleva ehto toteutuu vain, jos `kello` on samaan aikaan sekä suurempi tai yhtä suuri kuin 10 ja pienempi kuin 18. 


## Ehtorakenteet (tai)

Vuorokaudenajoista yö asettuu sekä järjestysnumeroltaan pienille että suurille tunneille. Tällainen ehto voidaan tarkistaa yhdistelemällä kaksi vertailua tai-operaatiolla:

```python
kello = 16

if kello >= 22 or kello < 7:
    # tähän lohkoon kirjoitettu koodi suoritetaan
    # jos kumpi tahansa ehdoista toteutuu!
    print("Hyvää yötä!")
```

Erilaisia ehtoja voidaan kirjoittaa myös ehtorakenteiden ulkopuolelle, jolloin niiden tulokset voidaan esimerkiksi sijoittaa muuttujiin:

```python
# vertailu suoritetaan ensin ja sen tulos asetetaan muuttujaan:
on_paiva = kello >= 10 and kello < 18
on_yo = kello >= 22 or kello < 7

# sama kuin aikaisemmin, mutta muuttujan avulla:
if on_paiva:
    print("Hyvää päivää!")

# sama kuin aikaisemmin, mutta muuttujan avulla:
if on_yo:
    print("Hyvää yötä!")
```

Vertailujen ympärillä voidaan käyttää aina myös sulkuja. Tarkoituksenmukainen välilyöntien ja sulkujen hyödyntäminen helpottaa koodin lukemista ja vähentää virheiden mahdollisuuksia.

Pythonissa on monista muista kielistä poiketen mahdollista vertailla yhtä arvoa samanaikaisesti kahteen muuhun arvoon: `a < b < c`. Tämän syntaksin avulla `on_paiva`-ehto voidaan ilmaista myös suoraviivaisemmin:

```python
on_paiva = 10 <= kello < 18
```


## Oikean kellonajan käyttäminen ohjelmassa 🕒

Edellisissä esimerkeissä esitetty kellonajan "kovakoodaaminen" tai kysyminen käyttäjältä eivät vastaa tavanomaisen ohjelman oikeaa toimintalogiikkaa. Oikeaa kellonaikaa voidaan käyttää esimerkiksi seuraavalla tavalla Pythonin `datetime `-moduulin avulla. 

Lisää ensin `import`-käsky tiedoston alkuun, jotta voit käyttää `datetime`-moduulia:

```python
from datetime import datetime
```

Sen jälkeen voit luoda `datetime`-olion ja käyttää sitä kellonajan selvittämiseksi:

```python
# Luodaan ajanhetki ja asetetaan se uuteen muuttujaan:
nykyhetki = datetime.now()

# Ajanhetki sisältää sekä päivän että kellonajan. Pyydetään kellonaika time-funktiolla:
aika = nykyhetki.time()

# Viimeisenä otetaan kellonajasta vain tunnit:
tunnit = aika.hour

if 10  <= tunnit < 18:
    print("Hyvää päivää!")
```



## Else-lohko

Usein ohjelmissa on tarpeen tehdä joko-tai-tyyppistä logiikkaa. Tämä tapahtuu helpoiten `if-else`-rakenteen avulla.

If-ehtorakenteen jälkeisessä vapaaehtoisessa `else`-lohkossa oleva koodi suoritetaan, mikäli if-lauseen ehto ei toteutunut:

```python
tunnit = 14

if 8 <= tunnit < 16:
    print("Työskentele ahkerasti!")
else:
    # Tässä lohkossa oleva koodi suoritetaan, jos 
    # edellä ollut if-ehto ei toteutunut 
    print("Vapaa-aika!")
```

`else`-avainsana koodilohkoineen kirjoitetaan aina heti `if`-lohkon jälkeen.


## if / elif / else

`elif`-lohkossa oleva koodi suoritetaan, jos edeltävien ehtolauseiden ehdot eivät ole toteutuneet ja tämän ehtorakenteen ehto toteutuu:

```python
kello = 16

if kello >= 22:     # tämä tarkastus tehdään aina ensin
    print("Hyvää yötä!")
elif kello >= 17:   # tämä ehto tarkastetaan, jos ensimmäinen oli epätosi
    print("Hyvää iltaa!")
else:
    # tänne päädytään, jos kaikki edellä olleet ehdot olivat epätosia
    print("Hyvää päivää!")
```

`if-elif-else` -ketjun ehtojen tarkastaminen päättyy aina ensimmäiseen `True`-arvon saaneeseen vertailuun.



## Useiden ehtojen käsittely sekä sisäkkäiset ehtolauseet

Seuraavat videot esittelevät toisiinsa liittyvien ehtojen tarkastamista if- ja elif-ehtolauseilla. Lisäksi ehdoissa olevia arvoja yhdistellään `or`-operaatiolla.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-21-of-44-Handling-Multiple-Conditions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [21 of 44] Handling Multiple Conditions - Microsoft Channel 9 Video"></iframe>


<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-22-of-44-Demo-Multiple-Conditions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [22 of 44] Demo: Multiple Conditions - Microsoft Channel 9 Video"></iframe>

<!--

## Monimutkaisemmat ehdot

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-23-of-44-Complex-Conditions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [23 of 44] Complex Conditions - Microsoft Channel 9 Video"></iframe>

## Demo: Monimutkaisemmat ehdot

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-24-of-44-Demo-Complex-Conditions/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [24 of 44] Demo: Complex Conditions - Microsoft Channel 9 Video"></iframe>

-->





## Extra: "Truthy" ja "Falsy" arvot

Pythonissa, toisin kuin monissa muissa kielissä, kaikkia kaikkia arvoja voidaan käyttää myös totuusarvojen paikalla ehtolauseissa.

Pääsääntöisesti kaikki nollaa vastaavat sekä tyhjät arvot ovat epätosia, kun taas muut arvot ovat tosia:

```python
if 'kissa':
    print('Kaikki ei-tyhjät merkkijonot ovat tosia!')

if 42:
    print('Kaikki nollasta poikkeavat numerot ovat tosia!')
```

Yllä oleva koodinpätkä tulostaa `Kaikki ei-tyhjät merkkijonot ovat tosia!` ja `Kaikki nollasta poikkeavat numerot ovat tosia!`.

Tämä ominaisuus on oikein käytettynä erittäin hyödyllinen, ja sillä voidaan myöhemmin esimerkiksi varmistaa, että lista ei ole tyhjä, ennen kuin sitä käytetään. Ominaisuuden kanssa on kuitenkin oltava tarkkana, koska esimerkiksi `'False'` on ei-tyhjä merkkijono, joka vastaa loogisesti arvoa `True`:

```python
taysi_ikainen = 'False'     # Merkkijono, ei totuusarvo!

if taysi_ikainen:
     print('Olet täysi-ikäinen!')
```

Koodi tulostaa siis virheellisesti `Olet täysi-ikäinen!`, koska muuttujassa on totuusarvon sijasta merkkijono.


## Videoiden lisenssi 

Tässä oppimateriaalissa hyödynnetyt Microsoftin [Python for Beginners -videosarjan](https://channel9.msdn.com/Series/Intro-to-Python-Development/) videot on lisensoitu [Creative Commons Attribution-Noncommercial-No Derivative Works 4.0 International](https://creativecommons.org/licenses/by-nc-nd/4.0/) -lisenssillä.
