
---
type: lecture
date: 2022-02-07T10:00:00+02:00
title: Python monitoimityökaluna
tldr: "Muutaman hyödyllisen valmiin Python-moduulin esimerkit"
thumbnail: 
__links__: 
    - url: /static_files/presentations/lec.zip
      name: notes
    - url: /static_files/presentations/code.zip
      name: codes
    - url: https://google.com
      name: slides
---

## "Python as a swiss army knife"

Seuraavissa esimerkeissä käytämme `curl`-komentoa, jonka voit asentaa Ubuntussa seuraavasti: `sudo apt install curl`. Lisätietoja komennosta löydät [Ubuntun manuaalista](https://manpages.ubuntu.com/manpages/focal/man1/curl.1.html).

```bash
$ curl https://raw.githubusercontent.com/theikkila/postinumerot/master/postcode_map_light.json
```

## JSON-työkalu: **json.tool**

Python 3:ssa on mukana `json.tool`-niminen moduuli, jonka avulla voidaan mm. muotoilla JSON-tietorakenteita helpommin luettavaan muotoon.

Kokeillaan seuraavaksi putkittaa curl-komennon tulostama sisentämätön JSON-tietorakenne `json.tool`-työkalulle:

```bash
$ curl https://raw.githubusercontent.com/theikkila/postinumerot/master/postcode_map_light.json | python3 -m json.tool
```

Sama voidaan tehdä myös tiedostolle (ensimmäinen komento lataa tiedoston paikalliseen hakemistoon):

```
$ curl https://raw.githubusercontent.com/theikkila/postinumerot/master/postcode_map_light.json > postinumerot.json
$ cat postinumerot.json | python3 -m json.tool
```

Data saadaan ladattua, muotoiltua ja tallennettua myös yhdellä rivillä:

```
$ curl https://raw.githubusercontent.com/theikkila/postinumerot/master/postcode_map_light.json | python3 -m json.tool > postinumerot.json
```

https://docs.python.org/3/library/json.html#json-commandline

## HTTP-palvelin: **http.server**

```
python3 -m http.server
```

https://developer.mozilla.org/en-US/docs/Learn/Common_questions/set_up_a_local_testing_server#running_a_simple_local_http_server


## Venv (Virtual environments)

Tällä kurssilla emme käytä Pythonin virtuaalisia ympäristöjä, koska kaikki harjoitukset ja esimerkit tehdään lähtökohtaisesti virtualisoimalla koko käyttöjärjestelmä. Jos sinulla on tarpeen kehittää samalla käyttöjärjestelmällä useita toisistaan riippumattomia Python-projekteja, näiden erittely omiksi ympäristöikseen `venv`-työkalulla on tedennäköisesti kannattavaa: https://docs.python.org/3/tutorial/venv.html


## Muut kurssilla myöhemmin käytettävät työkalut

* Pytest
* cProfile
* coverage