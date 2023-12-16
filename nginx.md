+++
title = 'Web-palvelinratkaisu'
date = 2023-12-16T18:02:13+02:00
draft = false
+++

# Nginx
[Nginx]('https://nginx.org/en/')

NGINX (lausutaan "engine X") on laajalti käytetty avoimen lähdekoodin web-palvelin, käänteinen proxy-palvelin ja kuormantasausjärjestelmä. Se tunnetaan erinomaisesta suorituskyvystään, skaalautuvuudestaan ja joustavuudestaan. Alun perin luotu ratkaisemaan C10k-ongelma (käsitellä 10 000 samanaikaista yhteyttä), NGINX on saavuttanut suosiota sen tehokkaan samanaikaisten pyyntöjen käsittelyn ansiosta.

Tärkeimmät NGINXin ominaisuudet ovat:

Web-palvelin: NGINX toimii web-palvelimena, joka vastaa HTTP-pyyntöihin ja palauttaa verkkosivuja tai muita resursseja pyytäjille.

Käänteinen proxy-palvelin: NGINX voi toimia käänteisenä proxy-palvelimena, joka välittää pyyntöjä taustalla oleville palvelimille ja välittää vastaukset takaisin pyytäjille. Tämä auttaa jakamaan kuormaa useiden palvelimien kesken ja parantaa suorituskykyä.

Kuormantasaus: NGINX voi toimia myös kuormantasausjärjestelmänä, joka jakaa saapuvat pyynnöt useiden palvelimien kesken tasapainottaen kuormaa. Tämä auttaa varmistamaan, että palvelimet eivät ylikuormitu ja että pyynnöt käsitellään tehokkaasti.

Staattiset tiedostot ja sisällön välitys: NGINX voi palvella staattisia tiedostoja suoraan ilman, että pyyntö joutuu ohjautumaan taustalla oleville sovelluspalvelimille. Se voi myös välittää dynaamisen sisällön sovelluspalvelimilta ja toimittaa sen pyytäjille.

NGINXin käyttökohteita ovat muun muassa verkkosivustot, sovellusten palvelinpuoli, API-rajapinnat, sisällön toimitusverkot (CDN), reititys ja kuormantasausjärjestelmät.

Visit the [Hugo](https://gohugo.io) website!

## Käyttötarkoitus tässä toteutuksessa
Tässä toteutuksessa Nginx-webpalvelinta käytetään Hugo CMS:n tuottamien staattisten sisältöjen tarjoamiseen http:n yli verkkosivuina.

## Kontin määrittely
Nginx-kontti mounttaa read-only oikeuksilla saman docker-volumen, johon Hugo on muodostanut staattiset sisällöt, ja tarjoaa tätä kohdetta sitten http:n yli. Kontille itselleen ei julkaista isäntäkoneelle portteja, vaan verkkosisällöt tarjotaan reverse-proxyn yli dns-osoitteella "myhugo.fbi.com".
