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

Tällä oppitunnilla perehdymme tarkemmin jo aikaisemmilta viikoilta tuttuihin merkkijonoihin. Opettelemme muotoilemaan merkkijonoja tehokkaammin Pythonin `f''`-syntaksilla, muuttamaan eri kirjaimet eri kokoisiksi sekä poimimaan merkkijonoista osia.


**Sisällysluettelo**

<div class="js-toc"></div>


**Suositeltavaa luettavaa**

* Ohjelmoinnin perusteet (mooc.fi): [Merkkijonojen käsittely](https://ohjelmointi-21.mooc.fi/osa-3/2-merkkijonojen-kasittely)
* Python for Everybody (py4e.com): [Strings](https://www.py4e.com/lessons/strings)
* Python documentation (docs.python.org): [Text Sequence Type — str](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)
* Python 3 – ohjelmointiopas: [sivut 15-20](http://urn.fi/URN:ISBN:978-952-335-622-1)




## Merkkijonot

Pythonin merkkijonoissa voidaan käyttää joko heittomerkkejä `'` tai lainausmerkkejä `"`. Sillä, kumpia merkkejä käytät merkkijonosi ympärillä, ei ole käytännössä merkitystä. Tärkeintä on käyttää systemaattisesti jompaa kumpaa tapaa.

Merkkijonojen yhdistämiseen voidaan käyttää `+` -merkkiä:

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

Python 3:ssa merkkijonojen yhdistelemiseksi on myös plus-merkkiä kätevämpiä tapoja, joita käsitellään seuraavalla videolla:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-11-of-44-Formatting-Strings/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [11 of 44] Formatting Strings - Microsoft Channel 9 Video"></iframe>


Soveltaen videolla esitettyä [formatted string literals](https://docs.python.org/3/tutorial/inputoutput.html#formatted-string-literals) -syntaksia, aiempi kaupungin nimen ja väkiluvun tulostaminen voidaan kirjoittaa kätevämmin:

```python
kaupunki = 'Helsinki'
vakiluku = 648_553

print(f'Kaupungissa {kaupunki} on {vakiluku} asukasta!')
```

Koodin tuloste on edelleen identtinen:

```
Kaupungissa Helsinki on 648553 asukasta!
```

Yllä muotoiluja sisältävän merkkijonon eteen on laitettu f-kirjain ja merkkijonoon sijoitettavat arvot on kirjoitettu aaltosulkujen sisään:

```python
muuttuja = 'mikä tahansa arvo'
muotoiltu = f'{muuttuja} voidaan sijoittaa merkkijonoon!'

print(muotoiltu)  # mikä tahansa arvo voidaan sijoittaa merkkijonoon!
```

Huomaa, että `'{muuttuja} voidaan sijoittaa merkkijonoon!'` ei toimi toivotulla tavalla ilman merkkijonon edessä olevaa `f`-kirjainta.

Seuraavalla videolla esitellään vielä yksi vaihtoehtoinen tapa arvojen sisällyttämiseksi merkkijonoihin, eli merkkijonojen `format`-metodi:

<iframe src="https://channel9.msdn.com/Series/Intro-to-Python-Development/Python-for-Beginners-12-of-44-Demo-Formatting-Strings/player" width="640" height="360" allowFullScreen frameBorder="0" title="Python for Beginners [12 of 44] Demo: Formatting Strings - Microsoft Channel 9 Video"></iframe>



## Kirjainkoon muuttaminen

Pythonissa on useita eri metodeja merkkijonon kirjainkoon vaihtamiseksi. Merkkijonon kaikki merkit saadaan isoiksi `upper()`-metodilla ja pieniksi `lower()`-metodilla:

```python
kaupunki = 'vantaa'

print(kaupunki.upper())       # 'VANTAA'
print(kaupunki.lower())       # 'vantaa'
```

`upper()` ja `lower()` ovat erityisen käteviä silloin, kun vertaat käyttäjän kirjoittamaa merkkijonoa johonkin ennalta tunnettuun. Et voi olla varma käyttäjän tekstin kirjainkoosta, mutta kutsumalla sille `lower()`-metodia saat merkkijonon varmasti oikeaan muotoon:

```python
vastaus = input('Haluatko jatkaa? ')

if vastaus.lower() == 'kyllä':
  print('jatketaan')
```

`title()`-metodi muuttaa jokaisen sanan alkukirjaimen isoksi ja muut pieniksi, kun taas `capitalize()` muuttaa vain merkkijonon ensimmäisen kirjaimen isoksi:

```python
elokuva = 'the dark knight'

print(elokuva.title())       # The Dark Knight
print(elokuva.capitalize())  # The dark knight
```

**Huomaa, että Pythonin merkkijonot ovat muuttumattomia.** Edellä mainitut metodit eivät siis muuta alkuperäistä merkkijonoa, vaan ne luovat siitä kopioita, jotka voit esimerkiksi tulostaa tai asettaa talteen muuttujaan.


## Tyhjien merkkien poistaminen alusta ja lopusta

Merkkijonojen metodi `strip()` poistaa tyhjät merkit merkkijonon alusta ja lopusta:

```python
siistitty = ' käyttäjän syöte voi päättyä tyhjiin merkkeihin '.strip()

print(siistitty) # 'käyttäjän syöte voi päättyä tyhjiin merkkeihin'
```

Huomaa, että tämäkään metodi ei muuta alkuperäistä merkkijonoa, vaan palauttaa siitä lyhennetyn kopion.


## Moniriviset merkkijonot

Moniriviset merkkijonot aloitetaan ja päätetään kolmella merkillä:

```python
loru = """Kuita nelisen kiurusta kesään

Pari kolme peipposesta

Västäräkistä vähintään puolitoista 

Pääskysestäkin vielä pitkään"""

print(loru)

# Loru: Maija Tuunila ja Antto Mäkinen. https://yle.fi/uutiset/3-9587146
```

Monirivisten merkkijonojen sisentämisessä on omat haasteensa, joita käsitellään esimerkiksi [tässä keskustelussa](https://stackoverflow.com/questions/2504411/proper-indentation-for-python-multiline-strings).



## Erikoismerkit

Kaikkia erikoismerkkejä ei voida esittää sellaisenaan merkkijonoissa. Esimerkiksi lainausmerkki merkkijonon sisällä voi sekoittua merkkijonon päättävään lainausmerkkiin. Erikoismerkit täytyykin esittää erityisten kontrollimerkkien avulla:

Syntaksi       | Kuvaus
---------------| ------
`\t`           | Lisää sisennyksen merkkijonoon
`\n`           | Lisää rivinvaihdon merkkijonoon
`\"`           | Lisää lainausmerkin merkkijonoon
`\\`           | Lisää kenoviivan merkkijonoon

Jos siis haluat esittää merkkijonossa esimerkiksi hakemistopolun 'C:\Users\Minä\Documents\', joudut käyttämään kenoviivan kohdalla kontrollimerkkiä:

```python
polku = 'C:\\Users\\Minä\\Documents\\'

print(polku)  # C:\Users\Minä\Documents\
```

Tapauksesta riippuen kenoviivoja joudutaan joskus laittamaan hyvin monia peräkkäin:

[![Backslashes](https://imgs.xkcd.com/comics/backslashes.png)](https://xkcd.com/1638/)

Kuva: [XKCD, Backslashes](https://xkcd.com/1638/). Creative Commons Attribution-NonCommercial 2.5


## Merkkijonon pituus

Pythonin funktio `len` palauttaa sille annetun merkkijonon pituuden. Välilyönnit, erikoismerkit ja rivinvaihdot lasketaan kukin yhden merkin pituisiksi, vaikka ne esitettäisiinkin lähdekoodissa kontrollimerkkien avulla:

```python
pituus = len('C:\\Users\\Minä\\Documents\\') # 24
```

## Merkit ja osajonot

Pythonissa merkkijonojen merkkejä ja osamerkkijonoja voidaan hakea hakasulkujen ja indeksien avulla. Huomaa, että indeksit alkavat aina nollasta:

```python
pvm = '2022-06-01'

print(pvm[0])   # '2'
print(pvm[1])   # '0'
```

Osamerkkijonoja puolestaan voidaan hakea antamalla yhden indeksin sijasta kaksi indeksiä: `[alku:loppu]`:

```python
pvm = '2022-06-01'

print(pvm[0:4])   # '2022'
print(pvm[5:7])   # '06'
```

Python sallii myös negatiiviset indeksit, jotka lasketaan merkkijonon lopusta lähtien:

```python
pvm = '2022-06-01'

print(pvm[-2])   # 0
print(pvm[-1])   # 1
```

Perehdy merkkijonojen leikkauksiin ja osanojoihin tarkemmin mooc.fi:n ohjelmoinnin perusteet -kurssin [Osajonot-kappaleen avulla](https://ohjelmointi-21.mooc.fi/osa-3/2-merkkijonojen-kasittely#osajonot)!



## Merkkijonojen toistaminen

Vähemmän käytetty, mutta toisinaan hyödyllinen ominaisuus Pythonin merkkijonojen parissa on merkkijonojen toistaminen kertomalla ne tietyllä kokonaisluvulla. Toistaminen voi tulla hyödyksi esimerkiksi silloin, kun haluat korostaa tai sisentää tulostettavaa tekstiä:

```python
otsikko = 'Merkkijonojen toistaminen'

print(otsikko)
print('=' * len(otsikko))
```

Yllä oleva koodi tulostaa ensin otsikon, ja sen jälkeen toistaa otsikon pituuden verran `=`-merkkiä:

```
Merkkijonojen toistaminen
=========================
```

Toisto-operaation tuloksena syntyy aivan tavallisia uusia merkkijonoja, joita voit muiden merkkijonojen tapaan yhdistellä, tulostaa tai käsitellä muilla tavoin:

```python
print('we will ' * 2 + 'rock you!') # we will we will rock you!
```

## Osajonojen etsiminen

Merkkijonojen sisältämiä osamerkkijonoja voidaan selvittää `in`-operaation avulla:

```python
print('java' in 'javascript')  # True
print('ham' in 'hamster')      # True
```

