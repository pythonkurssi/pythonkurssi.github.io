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

Kurssin suorittamiseksi tarvitset omalle tietokoneellesi Python-ohjelmointiympäristön, VS Code -editorin sekä Python-laajennoksen VS Code -editoriin. Saat käyttää myös muita työkaluja, mutta niihin ei voida tarjota käyttötukea.

Tällä oppitunnilla tutustumme Python-koodin kirjoittamiseen ja suorittamiseen komentorivillä sekä VS Code -sovelluskehittimessä. Käsittelemme numeerisia sekä tekstimuotoisia tietotyyppejä ja teemme yksinkertaista vuorovaikutusta käyttäjän kanssa tulosteiden ja syötteiden avulla. 

Lopuksi tunnilla opittuja asioita harjoitellaan ohjelmointitehtävien avulla.


**Oppitunnin aiheet**

1. Kurssin järjestelmät ja työkalut
1. Python-tulkin käyttäminen
1. Lähdekooditiedostot ja niiden suorittaminen
1. VS Code-editori
1. Muuttujat
1. Tekstin tulostaminen ja syötteen kysyminen käyttäjältä
1. Merkkijonot ja numerotyypit
1. Lukujen pyöristäminen
1. Kommentit


## Mikä Python on ja miksi käytämme sitä?

Seuraava video esittelee Pythonin käyttömahdollisuuksia ja sen perusperiaatteita.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-2-of-44-Introducing-Python/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [2 of 44] Introducing Python - Microsoft Channel 9 Video"></iframe>

[https://docs.microsoft.com/en-us/learn/modules/intro-to-python/2-what-is-python](https://docs.microsoft.com/en-us/learn/modules/intro-to-python/2-what-is-python)



## Pythonin asentaminen

Tallenna ja asenna Pythonin asennuspaketti Pythonin  viralliselta sivustolta [https://www.python.org/downloads/](https://www.python.org/downloads/). Valitse käyttöjärjestelmäsi mukaan Windows, Linux tai Mac OS versio.

Mikäli sinulla on jo valmiiksi asennettuna Python, voit käyttää sitä. Kurssilla käytettävän Python-version on kuitenkin oltava vähintään 3.7. Voit tarkistaa Python-asennuksesi version suorittamalla komentorivillä komennon `python --version`.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-3-of-44-Getting-Started/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [3 of 44] Getting Started - Microsoft Channel 9 Video"></iframe>



## Pythonin käyttäminen komentoriviltä: read–eval–print loop (REPL)

Pythonia voidaan käyttää suoraan komentoriviltä interaktiivisen tulkin avulla. Se onkin helpoin tapa tutustua kielen ominaisuuksiin. Python käynnistyy oletuksena interaktiivisessa tilassa, kun käynnistät sen komennolla `python`. Asennuksestasi riippuen Pythonin käynnistyskomento saattaa olla vaihtoehtoisesti `python3` tai `py`.

```
> python

Python 3.8.2 (tags/v3.8.2:7b3ab59, Feb 25 2020, 23:03:10) [MSC v.1916 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.

>>> 1 + 2 + 3
6
```

Interaktiivisella tulkilla lausekkeiden tuloksia ei tarvitse erikseen tulostaa, vaan sijoittamattomat arvot näytetään automaattisesit ruudulla.

Kokeile Pythonin laskuoperaatioita sivun [https://www.pythoncheatsheet.org/#Python-Basics](https://www.pythoncheatsheet.org/#Python-Basics) ohjeiden mukaan!


## Lähdekooditiedostot

Pythonin interaktiivinen tulkki on erittäin helppo ja nopea ympäristö erilaisten pienten kokeilujen tekemiseksi, mutta sinne kirjoittamasi ohjelmat eivät jää talteen myöhemmin suoritettaviksi. Ohjelmat kirjoitetaankin siksi erillisiin lähdekooditiedostoihin, jossa ne pysyvät tallessa useampia suoritus- ja muokkauskertoja varten.

Pythonin tapauksessa lähdekooditiedostot kirjoitetaan aina pienillä kirjaimilla ja tiedostojen päätteeksi kirjoitetaan `.py`. Lähdekooditiedostojen nimissä ei käytetä välilyöntejä, vaan välilyöntien tilalla käytetään alaviivaa `_`. Ääkköset korvataan a:lla ja o:lla: `lahdekooditiedoston_nimi.py`.

Python-lähdekooditiedostot ovat aivan tavallisia tekstitiedostoja, joita voitaisiin muokata jopa muistiolla. Ohjelmien kehittämiseksi on kuitenkin paljon parempia kehitystyökaluja, jotka avustavat koodin kirjoittamisessa ja löytävät automaattisesti koodissa olevia virheitä. 

Tällä kurssilla käytämme kehitysympäristönä (Integrated Development Environment, IDE) Visual Studio Codea, jonka asentamista käsitellään seuraavaksi.



## VS Coden asentaminen

Tallenna ja asenna Visual Studio Coden (VS Code) asennuspaketti sen viralliselta sivustolta [https://code.visualstudio.com/](https://code.visualstudio.com/). VS Code on saatavilla sekä Windowsille, Linuxille että Mac OS:lle.

Lisäksi tarvitset VS Coden Python-laajennoksen, jonka voit asentaa kätevästi extensions-näkymästä [Microsoftin ohjeen mukaisesti](https://code.visualstudio.com/docs/editor/extension-marketplace).

Seuraava video käy asennuksen läpi vaihe vaiheelta. Huomaa, että videolla esiintyvän vanhemman VS Code -version "extensions"-kuvake on hieman erinäköinen kuin nykyisessä versiossa. Laajennokset saa vaihtoehtoisesti näkyviin näppäinyhdistelmällä `Ctrl` + `Shift` + `X`.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-4-of-44-Configuring-Visual-Studio-Code/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [4 of 44] Configuring Visual Studio Code - Microsoft Channel 9 Video"></iframe>

Videolla esiintyvä suora asennuslinkki: [https://marketplace.visualstudio.com/items?itemName=ms-python.python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)




## Tekstin tulostaminen ruudulle

Tulostaminen tapahtuu `print`-funktiolla, jolle voidaan antaa tarvittaessa useampia tulostettavia arvoja:

```python
print('Hello world!')
```

Alla oleva video käsittelee kaksi tällä kurssilla keskeistä **funktiota**: `print` ja `input`. Näiden funktioiden avulla voimme näyttää käyttäjälle tekstiä ja pyytää käyttäjältä syötteitä.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-5-of-44-Using-Print/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [5 of 44] Using Print - Microsoft Channel 9 Video"></iframe>


## Lähdekooditiedostojen kanssa työskentely

Ohjelman kirjoittamiseksi tiedostoon ja sen suorittamiseksi tiedostosta tarvitset lähdekoodihakemiston ja lähdekooditiedostoja. Seuraava video ohjeistaa hakemiston ja tiedostojen luomisessa, sekä lähdekooditiedostojen suorittamisessa VS Code:n terminaalissa.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-6-of-44-Demo-Hello-World/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [6 of 44] Demo: Hello, World - Microsoft Channel 9 Video"></iframe>


## Syötteiden lukeminen

> *"Syöte tarkoittaa tietoa, jonka ohjelman käyttäjä antaa ohjelmalle. Pythonissa voimme lukea rivin käyttäjän antamaa syötettä `input`-komennolla. Komento näyttää samalla viestin käyttäjälle, jossa voi pyytää syötettä."*
>
> [Agile Education Research -tutkimusryhmä](https://www.helsinki.fi/en/researchgroups/data-driven-education). [https://ohjelmointi-21.mooc.fi/osa-1/2-tietoa-kayttajalta](https://ohjelmointi-21.mooc.fi/osa-1/2-tietoa-kayttajalta). [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.fi)

Alla olevassa koodiesimerkissä pyydetään käyttäjältä syötettä, eli nimeä, joka otetaan talteen `nimi`-muuttujaan:

```python
nimi = input('Mikä on nimesi? ')
print('Hei ' + nimi + '!')
```

Yllä olevassa esimerkissä esiintyy Python-kielen lausekkeiden lisäksi tekstidataa, eli kysymys `'Mikä on nimesi?'` sekä tervehdys `'Hei'`! Tällaista tekstidataa kutsutaan ohjelmoinnin yhteydessä **merkkijonoiksi**. 

Pythonin merkkijonoissa voidaan käyttää joko heittomerkkejä `'` tai lainausmerkkejä `"`.

Seuraava video esittelee tarkemmin muuttujien käyttämistä, merkkijonojen yhdistelyä sekä yhdisteltyjen merkkijonojen tulostamista:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-9-of-44-String-Concepts/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [9 of 44] String Concepts - Microsoft Channel 9 Video"></iframe>

Kuten huomasimme, merkkijonoja voidaan yhdistellä toisiinsa `+`-operaatiolla. Merkkijonoja voidaan myös asettaa muuttujiin ja voimme kysyä niitä käyttäjältä. Seuraava video esittelee esimerkin etu- ja sukunimien kysymiseksi sekä niiden muotoilemisen isoille alkukirjaimille tulostusta varten.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-10-of-44-Demo-Strings/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [10 of 44] Demo: Strings - Microsoft Channel 9 Video"></iframe>



## Kommentit

Pythonissa yksiriviset kommentit alkavat `#`-merkillä:

```python
# tämä on yksirivinen kommentti
```

Yksirivisiä kommentteja voidaan kätevästi kirjoittaa myös koodirivin loppuun. Mikäli tarvitset pidempiä kommentteja, ne voidaan kirjoittaa kolmen lainausmerkin sisään:

```python
""" tämä on monirivinen merkkijono, joita
    käytetään myös usein kommentteina """
```

Toisin kuin monissa muissa kielissä, Pythonissa kauttaviivalla ei voida aloittaa kommenttia:

```
// tämä ei ole kommentti!

/* tämäkään ei ole kommentti */
```

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-7-of-44-Comments/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [7 of 44] Comments - Microsoft Channel 9 Video"></iframe>



## Muuttujat ja tietotyypit

Pythonissa on lukuisia eri tietotyyppejä, joita voidaan hyödyntää lukuisin eri tavoin. Tyypillisiä tietotyyppejä ovat aikaisemmin näkemämme merkkijonot (str) sekä kokonaisluvut (int):

```python
kaupunki = 'Helsinki'
vakiluku = 648_553
```

Halutessamme voimme hyödyntää Pythonin `type`-funktiota tarkistaaksemme, minkä tyyppinen arvo tietyssä muuttujassa on tallennettuna:

```python
type(kaupunki) # str
type(vakiluku) # int
```

Eri tietotyyppien tiedostaminen ja taito muuttaa data toiseen tietotyyppiin ovat keskeisiä tällä kurssilla ja yleisesti ohjelmoitaessa. Yksi suoraviivainen esimerkki tietotyyppeihin liittyvässä logiikassa on `+`-operaatio, joka lukujen tapauksessa laskee kaksi lukua yhteen, mutta merkkijonojen tapauksessa liittää kaksi merkkijonoa peräkkäin.

Vaikka `+`-operaatio toimii sekä merkkijonojen että numeroiden kanssa, et voi käyttää sitä ristiin yhdistääksesi esimerkiksi numeroa merkkijonoon. Seuraavalla videolla käsitellään näitä tietotyyppejä sekä käyttäjältä saatujen syötteiden muuttamista numeroiksi `int` ja `float` funktioilla:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-13-of-44-Numeric-Data-Types/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [13 of 44] Numeric Data Types - Microsoft Channel 9 Video"></iframe>


## Lukujen tyyppimuunnokset ja pyöristäminen

Merkkijonoja voidaan muuttaa eri lukutyypeiksi, ja lukutyyppejä voidaan muuttaa toisiksi `int`- ja `float`-funktioilla:

```python
ika = int(input('Kerro ikäsi: '))
```

```python
alennusprosentti = 0.1 # 10 % alennus

hinta = float(input('Syötä pizzan hinta: '))

alennettu_hinta = hinta - (hinta * alennusprosentti)

print('Hinta alennuksen jälkeen: ' + str(alennettu_hinta))
```

Sama tulostus ei toimisi ilman `str`-muunnosta, koska Python ei salli katenoida lukuja sekä merkkijonoja:

```python
print('Hinta alennuksen jälkeen: ' + alennettu_hinta)

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "float") to str
```

Seuraavassa videossa esitellään käytännön esimerkin kautta yllä esitettyjen numeeristen syötteiden kysymistä, annettujen syötteiden muuntaminen numeroiksi laskuoperaatioita varten ja muuntaminen taas merkkijonoiksi tulostamista varten:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-14-of-44-Demo-Numbers/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [14 of 44] Demo: Numbers - Microsoft Channel 9 Video"></iframe>


## Liukuluvut ja niiden tarkkuus

Pythonissa on kaksi paljon käytettyä lukutyyppiä: `int` ja `float`. Int-tyypin avulla pystytään esittämään ainoastaan kokonaislukuja, kun taas float sisältää myös desimaaliosan. Python huolehtii lukujen muuttamisesta oikean tyyppisiksi automaattisesit, joten meidän ei usein tarvitse huolehtia siitä.

Liukuluvut esitetään aina käyttäen desimaalierottimena pistettä. Liukuluvun nimi tulee siitä, että numeron binääriesityksessä ei ole ennalta määrättyä määrää bittejä kokonaisosalle ja desimaaliosalle, vaan erottimen sijainti ja bittien määrä "liukuu" luvusta riippuen. 

Laskutoimitukset liukuluvuilla ovat erittäin nopeita. Tietokoneet käsittelevät mm. pelien grafiikkaa ja muuta matematiikkaa liukuluvuilla. Liukulukujen toteutuksesta johtuen niillä laskettaessa esiintyy kuitenkin usein pieniä laskuvirheitä, minkä vuoksi niitä ei tule käyttää täydellistä tarkkuutta vaativissa tarkoituksissa.

Kokeile suorittaa seuraava yhteenlasku. Minkä tuloksen saat?

```python
print(0.1 + 0.2) # minkä tuloksen saat?
```

Liukulukujen laskuvirhe ei niinkään liity Pythoniin, vaan yleisesti siihen, miten liukuluvut esitetään tietokoneen muistissa rajallisella määrällä ykkösiä ja nollia. Kaikkia lukuja ei vain ole mahdollista esittää täydellisellä tarkkuudella. Vastaavasti kymmenjärjestelmässä ei voida tarkasti esittää desimaalilukuna lukua 1/3.

💸 Tarkkuus- ja laskuvirheiden vuoksi esimerkiksi rahaa ei tulisi käsitellä liukulukuina. Hyvä taustoitus aiheeseen vaihtoehtoisine ratkaisuineen löytyy mm. [tästä StackOverflow-vastauksesta](https://stackoverflow.com/a/3730040).

## Lukujen pyöristäminen

Ohjelmissa halutaan usein rajata luvuista näytettävän desimaaliosan pituutta. Esimerkiksi hinnat esitetään tyypillisesti kahden desimaalin tarkkuudella. Pyöristäminen eri tarkkuuksille onnistuu `round`-funktiolla, jolle voidaan myös kertoa, kuinka monen desimaalin tarkkuudella pyöristys halutaan tehdä:

```python
>>> round(3.14)     # pyöristys lähimpään kokonaislukuun
3

>>> round(3.14, 1)  # pyöristys yhden desimaalin tarkkuudella
3.1
```

Usein lukujen pyöristäminen halutaan tehdä perinteisen pyöristämissäännön sijasta joko ylös- tai alaspäin lähimpään kokonaislukuun. Nämä onnistuvat Pythonin `math.ceil`- ja `math.floor`-funktioilla, esimerkiksi seuraavasti:

```python
import math  # ceil ja floor löytyvät math-moduulista

maalipurkin_koko = 2.7
maalin_tarve = 5.7

maalipurkkeja_ostettava = math.ceil(maalin_tarve / maalipurkin_koko) # ceil pyöristää aina ylöspäin

print('Tarvitset ' + str(maalipurkkeja_ostettava) + ' maalipurkkia')
```

Yllä olevassa ohjelmassa maalia tarvitaan liukulukuna `2.111111111111111` purkkia, mutta olettaen että maali myydään vain kokonaisina purkillisina, pyöristetään luku ylöspäin lähimpään kokonaislukuun:

```
Tarvitset 3 maalipurkkia
```

## Videoiden tekijänoikeudet 

Tässä oppimateriaalissa hyödynnetyt Microsoftin [Python for Beginners -videosarjan](https://channel9.msdn.com/Series/Intro-to-Python-Development/) videot on lisensoitu [Creative Commons Attribution-Noncommercial-No Derivative Works 4.0 International](https://creativecommons.org/licenses/by-nc-nd/4.0/) -lisenssillä.
