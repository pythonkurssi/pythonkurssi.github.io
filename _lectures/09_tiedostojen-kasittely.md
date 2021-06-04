---
type: lecture
date: 2022-03-28T10:00:00+03:00
title: Tiedostojen käsittely
tldr: "Tiedostojen lukeminen ja kirjoittaminen ohjelmallisesti."
thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---

> Usein kohtaamme tilanteen, jossa haluamme tallentaa muuttujien arvot koneelle myöhempää käyttöä varten, jotta ohjelman ja koneen voi sammuttaa välillä. Tällöin voisimme lukea muuttujien arvot suoraan koneelta ilman, että joudumme joka kerta aloittamaan ohjelman kirjoittamalla muuttujien tiedot koneelle. Tällaisten tilanteiden varalta Python tukee tiedostoihin kirjoittamista sekä niistä lukemista, joista puhumme tässä luvussa.
>
> Python käsittelee tiedostoja hyvin maanläheisellä ja yksinkertaisella tavalla. Avattu tiedosto on käytännössä Pythonin tulkille pitkä merkkijono, jota ohjelma voi käsitellä halutulla tavalla. Tähän liittyy kuitenkin tärkeä varoitus: Python-tulkki ei erota järjestelmäkriittisiä tiedostoja tavallisista tekstitiedostoista! Availe ja muuttele ainoastaan sellaisia tiedostoja, joista olet varma, että niitä voi ja saa muutella.
>
> *Vanhala, E., Nikula, U. (2020). [Python 3 – ohjelmointiopas versio 1.2.1](http://urn.fi/URN:ISBN:978-952-335-622-1). LUT-yliopisto. [CC BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/)*



**Sisällysluettelo**

<div class="js-toc"></div>


**Suositeltavaa luettavaa**

* Ohjelmoinnin perusteet (mooc.fi): [Datan käsittely](https://ohjelmointi-21.mooc.fi/osa-7/4-datan-kasittely)
* Python for Everybody (py4e.com): [Files](https://www.py4e.com/html3/07-files)
* Python 3 – ohjelmointiopas: [luku 6](http://urn.fi/URN:ISBN:978-952-335-622-1)


## Tiedostojen lukeminen ja kirjoittaminen

Suurten tiedostojen käsittely ohjelmallisesti saattaa aiheuttaa merkittäviä suorituskykyhaasteita:

* kirjoittaessa tiedostoon yksittäiset kirjoitus- ja lukuoperaatiot ovat hitaita
* luettaessa tiedostosta koko sisällön lukeminen kerralla voi viedä paljon muistia.

Suorituskykyhaasteiden vuoksi tiedostoja käsitellään usein erilaisten puskurien avulla:

* puskuriin voidaan kirjoittaa dataa pienissäkin palasissa, mutta puskurin sisältö tallennetaan levylle isommissa erissä
* tiedostoa luetaan kerralla isompi erä puskuriin, josta siitä hyödynnetään esim. rivi kerrallaan.

Vastaavia haasteita ja ratkaisuja hyödynnetään myös mm. tietoliikenneyhteyksissä.

Jos kirjoitettavaa tai luettavaa on kohtuullinen määrä, ei puskureita ole välttämätöntä käyttää. Tiedosto voidaan kirjoittaa kerralla esimerkiksi listasta merkkijonoja tai tiedosto voidaan lukea listaksi merkkijonoja.

Tällä oppitunnilla käsittelemme pieniä tiedostoja emmekä huomioi suorituskykynäkökulmaa.

## Tiedoston lukeminen: with ja open

> Hyvä tapa käsitellä tiedostoja Pythonissa on käyttää with-lausetta, jonka alkurivi avaa tiedoston. Tämän jälkeen tulee lohko, jonka sisällä tiedostoa voi käsitellä. Lohkon jälkeen tiedosto sulkeutuu automaattisesti, eikä sitä voi enää käsitellä.
>
> Esimerkiksi seuraava koodi lukee ja tulostaa tiedoston sisällön:
>
>     with open("esimerkki.txt") as tiedosto:
>         sisalto = tiedosto.read()
>         print(sisalto)
>
> *[Agile Education Research -tutkimusryhmä](https://www.helsinki.fi/en/researchgroups/data-driven-education). [Tiedostojen lukeminen](https://ohjelmointi-21.mooc.fi/osa-6/1-tiedostojen-lukeminen). [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.fi)*

Tällä kurssilla käytämme tiedostoja aina edellä mainitun `with x as y` -rakenteen avulla. Vaikka itse tiedosto suljetaa koodilohkon jälkeen, jää lohkossa luettu merkkijono oman koodimme käyttöön tämän rakenteen jälkeen.


## read, readline ja readlines

Kun tiedosto on avattu `open`-funktiolla, sen sisältöä voidaan lukea muutamalla eri metodilla:

* **read**

    Lukee koko tiedoston kerralla yhdeksi merkkijonoksi.

* **readline**

    Lukee tiedostosta seuraavan rivin uudeksi merkkijonoksi. Tätä metodia voidaan kutsua toistuvasti koko tiedoston lukemiseksi rivi kerrallaan.

* **readlines**

    Lukee koko tiedoston kerralla, ja palauttaa **listan**, jossa kukin tiedoston rivi on omana merkkijononaan.

[https://docs.python.org/3/library/io.html#io-overview](https://docs.python.org/3/library/io.html#io-overview)

## CSV-tiedostot (comma-separated values)

Taulukkomuotoisen tiedon tallentamiseen yksinkertaisina tekstitiedostoina käytetään usein CSV-tiedostoja:

> *"CSV on toteutukseltaan tekstitiedosto, jonka taulukkorakenteen eri kentät on eroteltu toisistaan pilkuilla ja rivinvaihdoilla. Jos jokin kenttä sisältää erikoismerkkejä, kyseinen kenttä ympäröidään pystysuorilla lainausmerkeillä ("). Ensimmäisellä rivillä voi olla kenttien selitykset samassa muodossa kuin mitä itse tiedot ovat."*
>
> Wikipedia. CSV. https://fi.wikipedia.org/wiki/CSV

[Wikipedian esimerkissä](https://fi.wikipedia.org/wiki/CSV) autojen tiedot on esitetty tallennettuna seuraavassa CSV-muodossa:

```
Vuosi,Merkki,Malli,Pituus
1997,Ford,E350,2.34
2000,Mercury,Cougar,2.38
```

Sama data on esitettävissä myös taulukkomuodossa:

Vuosi   | Merkki    | Malli     | Pituus
--------|-----------|-----------|-------
1997    | Ford      | E350      | 2.34
2000    | Mercury   | Cougar    | 2.38

Koska CSV-tiedostot on helposti koneluettavia ja -kirjoitettavia, hyvin monet ohjelmat tukevat niitä tiedon tallennusmuotonaan.

## Esimerkki CSV-tiedoston lukemisesta

Oletetaan että edellä esitelty CSV-tiedosto on tallennettu tiedostoon [autot.csv](autot.csv), joka sijaitsee samassa hakemistossa Python-koodimme kanssa. Voimme nyt avata tiedoston Pythonissa ja lukea sen sisällön seuraavasti:

```python
with open('autot.csv') as tiedosto:
    rivit = tiedosto.readlines()

print(len(rivit)) # 3
print(rivit[0]) # Vuosi,Merkki,Malli,Pituus

for autorivi in rivit[1:]:  # jätetään otsikkorivi välistä
    # pilkotaan jokainen tieto omaan muuttujaansa
    vuosi, merkki, malli, pituus = autorivi.split(',')
    
    print(f'{merkki} {malli} ({vuosi})')
```

Yllä oleva ohjelma tulostaa tiedostosta luetut tiedot viimeisellä koodirivillä määritellyssä muodossa:

```
Ford E350 (1997)
Mercury Cougar (2000)
```

## MerkistÃ◦t (merkistöt)

Eri kielialueilla on perinteisesti ollut tarve hyvin erilaisille kirjainmerkeille. Siksi niissä on kehitetty erilaisia merkistöjä, joissa tietyllä bittijonolla on keskenään eri merkitys. Oletkin varmasti törmännyt erilaisissa asiayhteyksissä kummallisiin erikoismerkkeihin sanoissa, joissa kuuluisi olla ääkkösiä.

Nykypäivänä suositellaan käytettäväksi UTF-8 -nimistä merkistöä, joka sisältää merkittävän osan maailmalla käytetyistä merkeistä, kuten 請 ja ✌️. UTF-8:n suosio on noussut erittäin voimakkaasti ja myös tämä tiedosto on kirjoitettu UTF-8:lla.

![Share of web pages with different character encoding](https://upload.wikimedia.org/wikipedia/commons/c/c4/Utf8webgrowth.svg)

By Chris55 - Own work, CC BY-SA 4.0, [https://commons.wikimedia.org/w/index.php?curid=51421096](https://commons.wikimedia.org/w/index.php?curid=51421096)

Jotta ohjelmasi toimisi luotettavasti eri suoritusympäristöissä, kannattaa aina tiedostoja luettaessa ja kirjoitettaessa määritellä käytettävä merkistökoodaus:

```python
with open('autot.csv', encoding='utf-8') as tiedosto:
    rivit = tiedosto.readlines()
```

## Tiedostoon kirjoittaminen

Tiedostoon voidaan kirjoittaa melko samankaltaisesti kuin miten luimme tiedostosta. Tässäkin tapauksessa käytetään Pythonin `open`-funktiota, mutta tällä kertaa joudumme määrittelemään myös tiedoston tilan (mode). Tiedoston käsittelytila on oletuksena `'r'` eli luku, mutta antamalla tiedoston nimen jälkeen funktiolle parametrin `'w'` tiedosto avataan kirjoitettavaksi:

```python
with open('tallennettava.txt', 'w') as tiedosto:
    # nyt tiedostoon voidaan kirjoittaa!
```

Jos määritettyä tiedostoa ei ole olemassa, Python luo sen automaattisesti. Itse kirjoittaminen tapahtuu tiedoston ollessa avoinna `write`-metodilla:

```python
with open('tallennettava.txt', 'w', encoding='utf-8') as tiedosto:
    tiedosto.write('Kun tiedosto avataan "w"-parametrin kanssa,\n')
    tiedosto.write('siihen voidaan myös kirjoittaa.\n')
    tiedosto.write('Kirjoittaminen tapahtuu write-metodilla!\n')
```

Tiedostoja käsiteltäessä kannattaa aina määritellä käytettävä merkistö, kuten yllä olevassa esimerkissä on tehty. Koodin suorituksen jälkeen hakemistoon on ilmestynyt tiedosto *tallennettava.txt*, joka on sisällöltään seuraava:

```
Kun tiedosto avataan "w"-parametrin kanssa,
siihen voidaan myös kirjoittaa.
Kirjoittaminen tapahtuu write-metodilla!
```


## Koodaustehtävä

Kirjoita ohjelma `word_count.py`, joka kysyy käyttäjältä tiedoston nimeä ja tulostaa kyseisessä tiedostossa olevien rivien, sanojen ja merkkien määrän. Voit olettaa luettavan tiedoston olevan samassa hakemistossa Python-koodisi kanssa.

Riveksi lasketaan myös tyhjät rivit ja merkeiksi myös esimerkiksi välilyönnit. Sanojen laskemiseksi voit käyttää `split`-metodia, jolla pilkot kunkin rivin välilyöntien kohdalta.

```
Anna tiedoston nimi: loremipsum.txt

Tiedostossa on:
2 riviä
8 sanaa
55 merkkiä

```

Yllä olevassa esimerkkisuorituksessa luettiin seuraava tekstitiedosto *loremipsum.txt*:

```
Lorem ipsum dolor sit amet,
consectetur adipiscing elit.
```

