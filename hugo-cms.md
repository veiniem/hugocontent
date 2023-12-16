+++
title = 'Content management -palveluratkaisu (CMS)'
date = 2023-12-16T17:28:27+02:00
draft = false
+++

# Hugo CMS
[HugoCMS]('https://gohugo.io/')

Hugo CMS on staattisen verkkosivujen generaattori, joka on suunniteltu nopeaan ja tehokkaaseen verkkosivujen luomiseen. Se on avoimen lähdekoodin CMS (sisällönhallintajärjestelmä) ja se perustuu Go-ohjelmointikieleen.

Hugo CMS-ohjelmisto toimii niin, että se luo verkkosivut valmiiksi ennen niiden julkaisua. Se rakentaa sivut staattisiksi tiedostoiksi, mikä tarkoittaa, että verkkosivujen lataaminen on nopeaa ja sivujen suorituskyky on erinomainen. Tämä eroaa perinteisistä CMS-järjestelmistä, jotka usein toimivat dynaamisesti ja vaativat tietokantaa sivujen sisällön tallentamiseen.

Hugo CMS tarjoaa käyttäjilleen helppokäyttöisen ja joustavan käyttöliittymän verkkosivujen hallintaan. Sen avulla voit luoda ja muokata sisältöä sivuilla käyttäen Markdown-syntaksia tai HTML:ää. Se tarjoaa myös monipuoliset teema- ja mukauttamismahdollisuudet, joiden avulla voit räätälöidä verkkosivustosi ulkoasua ja toiminnallisuutta omien tarpeidesi mukaan.

Hugo CMS on suosittu kehittäjien keskuudessa sen nopeuden, turvallisuuden ja yksinkertaisuuden vuoksi. Se soveltuu erinomaisesti kevyiden ja staattisten verkkosivustojen, kuten blogien, henkilökohtaisten sivustojen tai yrityssivustojen, luomiseen.

## Käyttötarkoitus tässä toteutuksessa
Tässä toteutuksessa Hugoa käytetään staattisten verkkosisältöjen generointiin näiden Markdown-tiedostojen sisältöjen mukaisesti. Markdownien sisältö käännetään verkkosisällöksi Hugon avulla, jonka jälkeen tuotetut staattiset sisällöt muodostetaan Docker-isännän tiedostojärjestelmään näiden tarjoamiseksi sitten web-palveluna.

## Kontin määrittely
Toteutuksessa käytetty Hugo-containerimage käyttää pohjakuvana Alpine Linuxia, jonka päälle Hugo on asennettu. Kontin käynnistyksen yhteydessä päivitetyt sisällöt haetaan käännettäväksi tästä repositoriosta git:llä. Dockerimagessa viimeinen CMD-määritys on bash-komento "sleep 300", jonka myötä kontti siirtyy exited-tilaan 5 minuuttia käynnistymisensä jälkeen. Tämän lisäksi docker-compose.yml:ssä on määritetty kontti uudelleenkäynnistymään automaattisesti sen sammumisen yhteydessä, minkä myötä päivitetyt sisällöt haetaan ja käännetään näytettäväksi aina viiden minuutin välein.
