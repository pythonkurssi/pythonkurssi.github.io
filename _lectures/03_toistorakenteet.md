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

# Toistorakenteet

Ehtorakenteiden tavoin toistorakenteilla voidaan vaikuttaa koodin suorituksen etenemiseen. Toistorakenteiden avulla tietyt koodirivit voidaan toistaa eri logiikoilla tai tarvittaessa jopa "ikuisesti". 

Tällä opetusviikolla harjoittelemme pääasiassa koodin toistamista tietyn määrän kertoja, toiston keskeyttämistä, sekä käymään läpi kokonaislukuja. Toistorakenteita hyödynnetään myöhemmin myös listojen ja taulukoiden yhteydessä, jolloin käymme läpi niissä olevia arvoja yksitellen.


**Sisällysluettelo**

<div class="js-toc"></div>


**Suositeltavaa luettavaa**

* Ohjelmoinnin perusteet (mooc.fi): [Ehdot silmukoissa](https://ohjelmointi-21.mooc.fi/osa-3/1-ehdot-silmukoissa)
* Python for Everybody (py4e.com): [Loops and Iterations](https://www.py4e.com/lessons/loops)
* Python documentation (docs.python.org): [For statements](https://docs.python.org/3/tutorial/controlflow.html#for-statements)
* Python 3 – ohjelmointiopas: [luku 4](http://urn.fi/URN:ISBN:978-952-335-622-1)


## While-toistorakenne

While-toistorakenne on yksinkertaisin tapa toistaa koodia Pythonilla. `while`-avainsanan jälkeen kirjoitetaan vain toistoehto ja sen jälkeen koodilohko, jota toistetaan niin kauan, kuin ehto on tosi:

```python
while ehto:
    # Toistetaan, jos ehto == True ja 
    # lopetetaan, kun ehto == False
```

Vuokaaviona while-toistorakenteen logiikka on seuraava:

![While loop flow diagram](/_images/While-loop-diagram.svg)

Kuva: P. Kemp. While loop flow diagram. CC0. [Wikipedia](https://commons.wikimedia.org/w/index.php?curid=894438)


### while vs. if

Syntaksin puolesta `while` ja `if` ovat hyvin samankaltaiset:

```python
if ehto:
    # Suoritetaan kerran, jos ehto == True
```

```python
while ehto:
    # Toistetaan, jos ehto == True ja 
    # lopetetaan, kun ehto == False
```

Ehtorakenteesta poiketen toistorakenteessa toistettavassa lohkossa tehdään tyypillisesti muutoksia, jotka vaikuttavat tarkistettavaan ehtoon. Näiden muutosten avulla toisto saadaan päättymään, kun haluttu logiikka on saatu suoritettua valmiiksi.


## Ehdon muuttaminen toistettavassa koodilohkossa

Jotta toistoehto muuttuisi jossain vaiheessa epätodeksi, tehdään toistettavassa koodilohkossa tyypillisesti operaatioita, jotka vaikuttavat toistoehtoon. Operaatio on usein jonkin muuttujan arvon kasvattaminen.

Kun koodia halutaan suorittaa tietty määrä kertoja, käytetään tyypillisesti muuttujaa, joka pitää kirjaa suorituskerroista. Tällaisesta muuttujasta käytetään myös termiä **askeltaja**. Seuraavassa esimerkissä `tunnit`-muuttujaa käytetään rajoittamaan suorituskertoja siten, että ruudulle tulostetaan vuorollaan luvut nollasta kahteenkymmeneen kolmeen:

```python
tunnit = 0

while tunnit < 24:
    # tämä koodilohko suoritetaan tunnit-muuttujan 
    # arvoilla nollasta 23:een
    print(tunnit)

    # kasvatetaan muuttujan arvoa seuraavaa kierrosta varten:
    tunnit = tunnit + 1
```

Toistettavan lohkon lopussa esiintyvä `tunnit = tunnit + 1` kasvattaa muuttujan arvoa aina yhdellä seuraavaa toistokierrosta varten. Lopulta, kun tunnit-muuttujan arvo ei enää läpäise toistoehtoa, toisto päättyy ja koodin suoritus jatkuu toistorakenteen alapuolelta.

Pythonissa on muuttujan arvon kasvattamiseksi myös toinen syntaksi: `tunnit += 1`, joka kasvattaa `tunnit`-muuttujan arvoa `+=`-operaattorin oikealle puolelle määritellyn luvun verran:

```python
tunnit = 0

while tunnit < 24:
    print(tunnit)
    tunnit += 1
```


## While-toistorakenteen hyödyntäminen

Toistoa tarvitaan hyvin monenlaisten ongelmien ratkaisemiseksi. Ajatellaan esimerkiksi, että haluaisimme määritellä verkkosivulle `<select>`-elementin, jonka avulla käyttäjä voi rajata myynti-ilmoitusten hakutyökalun hintaa. 

Tämän yksinkertaistetun esimerkin avulla voit valita hinnan ylä- ja alarajan 500 euron välein väliltä 0-5&nbsp;000 euroa:

<fieldset>
    <legend>Hinta</legend>
    <select name="min">
        <option>Minimi</option>
        <option value="0">0 €</option>
        <option value="500">500 €</option>
        <option value="1000"> 1 000 €</option>
        <option value="1500"> 1 500 €</option>
        <option value="2000"> 2 000 €</option>
        <option value="2500"> 2 500 €</option>
        <option value="3000"> 3 000 €</option>
        <option value="3500"> 3 500 €</option>
        <option value="4000"> 4 000 €</option>
        <option value="4500"> 4 500 €</option>
        <option value="5000"> 5 000 €</option>
    </select> - 
    <select name="max">
        <option>Maksimi</option>
        <option value="0">0 €</option>
        <option value="500">500 €</option>
        <option value="1000"> 1 000 €</option>
        <option value="1500"> 1 500 €</option>
        <option value="2000"> 2 000 €</option>
        <option value="2500"> 2 500 €</option>
        <option value="3000"> 3 000 €</option>
        <option value="3500"> 3 500 €</option>
        <option value="4000"> 4 000 €</option>
        <option value="4500"> 4 500 €</option>
        <option value="5000"> 5 000 €</option>
    </select>
</fieldset>

Koodin idea on peräisin [nettiauto.com:in](https://www.nettiauto.com/) hakutyökalusta, jossa haettavan auton hintaa voidaan rajoittaa vastaavalla tavalla.

Yllä olevat HTML-valintaelementit muodostetaan [select](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select-) sekä [option](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/option)-tagien avulla kutakuinkin seuraavasti:

```html
<select name="min">
    <option>Minimi</option>
    <option value="0">0 €</option>
    <option value="500">500 €</option>
    <option value="1000"> 1 000 €</option>
    <option value="1500"> 1 500 €</option>
    <!-- ... -->
    <option value="5000"> 5 000 €</option>
</select>
```

Mikäli hintarajaus haluttaisiin tehdä esimerkiksi nollasta sataan tuhanteen euroon, tulisi HTML-koodista "kovakoodattuna" valtavan pitkä ja hankalasti ylläpidettävä. Sen sijaan voimme kirjoittaa toistorakenteen, jossa `<option>`-elementtejä toistetaan eri suuruisten summien kanssa. Ylempänä esitetystä esimerkistä poiketen toistossa käsiteltävä arvo ei nyt kasvakaan aina yhdellä, vaan esimerkiksi 500:lla.


```python
hinta = 0

print('<select name="min">')
print('    <option>Minimi</option>')

while hinta <= 5_000:
    print('    <option value="' + str(hinta) + '">' + str(hinta) + ' €</option>')
    hinta += 500

print('</select>')
```

## For-toistorakenne

> "`for`-rakenne on toinen Pythonin kahdesta tavasta toteuttaa toistorakenne. `for`-lause eroaa
`while`-rakenteesta kolmella merkittävällä tavalla. 
>
> Ensinnäkin `for`-lauseen kierrosmäärä on tiedettävä lauseen suorituksen alkaessa.
>
> Toiseksi `for`-lausetta voi käyttää monialkioisten rakenteiden kuten listojen alkioiden läpikäymiseen. 
>
> Kolmanneksi `for`-lause on suunniteltu etukäteen tiedettävien asioiden läpikäyntiin, eikä sen kanssa voida käyttää useita lopetusehtoja.
>
> Tällä kertaa keskitymme for-lauseen käyttämiseen sen perinteisemmässä
muodossa eli silmukoiden tekemisessä. Listoihin ja niiden läpikäyntiin palaamme
myöhemmin."
>
> Vanhala, E., Nikula, U. (2020). Python 3 – ohjelmointiopas versio 1.2.1. LUT-yliopisto. Saatavilla: [http://urn.fi/URN:ISBN:978-952-335-622-1](http://urn.fi/URN:ISBN:978-952-335-622-1)

### Toiston rajojen määrittely: range

Jos haluamme käydä läpi numerot väliltä 0-23, kuten teimme `while`-esimerkissä, se tehdään käymällä läpi kyseinen joukko numeroita. Sen sijaan, että kasvattaisimme lukua aina yhdellä ja vertaisimme uutta lukua toistoehtoon, tarvitsemme valmiin joukon numeroista jo toistoa aloitettaessa.

Tämä voidaan tehdä suoraviivaisesti Pythonin valmiin `range`-tyypin avulla:

> "The range type represents an immutable sequence of numbers and is commonly used for looping a specific number of times in for loops."
> 
> Python documentation. Range. [https://docs.python.org/3/library/stdtypes.html#typesseq-range](https://docs.python.org/3/library/stdtypes.html#typesseq-range)

`range`:lle voidaan antaa yhdestä kolmeen parametria: **start**, **stop** ja **step**. Jos haluamme käydä läpi kaikki arvot väliltä 0-23, muodostamme `range`:n seuraavasti: `range(0, 24, 1)`. **Huomaa, että *stop*-arvo on yläraja, joka ei enää tule mukaan lukujoukkoon**.

Parametreista **start** ja **step** ovat valinnaisia. Jos emme anna ensimmäistä parametria, alkavat luvut nollasta. Vastaavasti jos jätämme viimeisen parametrin pois, kasvatetaan lukuja aina yhdellä. Näin numerojoukkomme voidaan kirjoittaa myös lyhyemmin: `range(24)`.

### Koodin toistaminen for-rakenteella

For-toistorakenteen syntaksi on varsin suoraviivainen:

```python
for muuttuja in arvojoukko:
    # toistettava koodi
```

Toisin kuin `while`-rakenteessa, sinun ei tarvitse huolehtia muuttujan kasvattamisesta eikä koodi tarvitse lopetusehtoa. Aikaisempi vuorokauden tunnit toistava koodimme onkin `for`-muodossa esitettävissä seuraavasti:

```python
for tunnit in range(24):
    # tunnit saa vuorollaan jokaisen arvon 0-23
    print(tunnit)
```

Koodi tulostaa edelleen luvut 0-23:

```
0
1
2
...
22
23
```

`range` ei suinkaan ole ainoa arvojoukko jota käytetään Pythonissa for-toistorakenteissa. Palaamme kurssilla myöhemmin myös muihin tapoihin, joilla voimme käydä läpi arvoja toistorakenteella:

```python
for paiva in ('ma', 'ti', 'ke', 'to', 'pe', 'la', 'su'):
    print(paiva)
```

## Yhteenveto: for, while ja range

Seuraava video käy konkreettisesti läpi edellä esitetyt toistorakenteet ja niiden käyttötapoja. Videolla pohditaan myös mitkä ovat eri toistolauseiden vahvuudet erilaisten ongelmien ratkaisussa.

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-27-of-44-Loops/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [27 of 44] Loops - Microsoft Channel 9 Video"></iframe>

<!-- Seuraavalla videolla sovelletaan toistoa listojen kanssa. Listat käsitellään tällä kurssilla vasta myöhemmin, mutta voit jo etukäteen perehtyä pintapuolisesti listatyyppisten arvojen läpikäyntiin for-toistorakenteella -->

<!--<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-28-of-44-Demo-Loops/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [28 of 44] Demo: Loops - Microsoft Channel 9 Video"></iframe> -->


## For-toistorakenteen hyödyntäminen

Toteutetaan vertailun vuoksi toistorakenne, joka muodostaa [nettiauto.com:in](https://www.nettiauto.com/) hakutyökalun mukaisen vuosiluvun valintaan käytettävän HTML-rakenteen. Aikaisemmasta esimerkistä poiketen tässä elementissä luvut ovat **laskevassa järjestyksessä**, ja suurin arvo vaihtuu aina kuluvan vuoden mukaan:

<fieldset>
    <legend>Vuosimalli</legend>
    <select name="min">
        <option>Minimi</option>
        <option value="2022">2022</option>
        <option value="2021">2021</option>
        <option value="2020">2020</option>
        <option value="2019">2019</option>
        <option value="2018">2018</option>
        <option value="2017">2017</option>
        <option value="2016">2016</option>
        <option value="2015">2015</option>
        <option value="2014">2014</option>
        <option value="2013">2013</option>
        <option value="2012">2012</option>
        <option value="2011">2011</option>
        <option value="2010">2010</option>
    </select> - 
    <select name="max">
        <option>Maksimi</option>
        <option value="2022">2022</option>
        <option value="2021">2021</option>
        <option value="2020">2020</option>
        <option value="2019">2019</option>
        <option value="2018">2018</option>
        <option value="2017">2017</option>
        <option value="2016">2016</option>
        <option value="2015">2015</option>
        <option value="2014">2014</option>
        <option value="2013">2013</option>
        <option value="2012">2012</option>
        <option value="2011">2011</option>
        <option value="2010">2010</option>
    </select>
</fieldset>

Yllä olevat HTML-valintaelementit muodostetaan [select](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select-) sekä [option](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/option)-tagien avulla kutakuinkin seuraavasti:

```html
<select name="min">
    <option>Minimi</option>
    <option value="2022">2022</option>
    <option value="2021">2021</option>
    <!-- ... -->
    <option value="2011">2011</option>
    <option value="2010">2010</option>
</select>
```

For-toistorakenteessa läpikäytävät arvot ovat nyt vuosilukuja, joiden alkuarvo on esimerkiksi 2022. Toistossa lukuja käydään läpi laskevassa järjestyksessä aina vuoteen 2010 asti. Hyödyntäen `for`-toistorakennetta ja `range`-tyypin avulla. Alkuarvoksi (start) asetetaan **2022**, loppuarvoksi (stop) vuosi **2009** ja askeleeksi (step) **-1**: `range(2022, 2009, -1)`.

```python
print('<select name="min">')
print('    <option>Minimi</option>')

for vuosi in range(2022, 2009, -1):
    print('    <option value="' + str(vuosi) + '">' + str(vuosi) + '</option>')

print('</select>')
```

Yllä olevassa koodissa vuosilukujen ylärajaksi on **kovakoodattu** vuosi 2022. Oikeassa sovelluksessa vaihtelevia vuosilukuja ei kannata kovakoodata, vaan ne kannattaa muodostaa ohjelmallisesti. Nykyinen vuosiluku voidaan selvittää Pythonin `datetime`-moduulin avulla esimerkiksi seuraavasti:

```python
from datetime import datetime
nyt = datetime.now()
nykyinen_vuosi = nyt.date().year 
```

Yllä olevaa aikalogiikkaa hyödyntäen aikaväli määritettäisiin seuraavasti:

```python
for vuosi in range(nykyinen_vuosi, 2009, -1):
    # ...
```


## Toistosta poistuminen eli **break**

Varsin usein haluamme suorittaa koodia toistaiseksi, kunnes käyttäjä esimerkiksi antaa tietyn syötteen. Tällöin voi olla hyödyllistä tehdä "ikuinen silmukka" eli:

```python
while True:
    # toistettava koodi
```

Jotta ikuisesta toistosta voidaan lopulta poistua, voimme käyttää `break`-komentoa, joka keskeyttää sitä ympäröivän toistorakenteen välittömästi.

```python
while True:
    # toistettava koodi
    vastaus = input('Mikä komento lopettaa toiston? ')
    if vastaus == 'break':
        print('Oikein!')
        break
    else:
        print('Väärin...')

print('Ohjelma päättyy')
```


## Videoiden lisenssi 

Tässä oppimateriaalissa hyödynnetyt Microsoftin [Python for Beginners -videosarjan](https://channel9.msdn.com/Series/Intro-to-Python-Development/) videot on lisensoitu [Creative Commons Attribution-Noncommercial-No Derivative Works 4.0 International](https://creativecommons.org/licenses/by-nc-nd/4.0/) -lisenssillä.
