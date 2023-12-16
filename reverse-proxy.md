+++
title = 'Käänteinen välityspalvelin (reverse-proxy)'
date = 2023-12-16T18:12:31+02:00
draft = false
+++

# Traefik
[Traefik]('https://traefik.io/traefik/')

Traefik on avoimen lähdekoodin käänteinen proxy-palvelin ja kuormantasausjärjestelmä, joka on suunniteltu helpottamaan ja tehostamaan konttien ja mikropalveluarkkitehtuurin hallintaa. Se toimii liikenteen välittäjänä sovellusten ja taustalla olevien palvelinten välillä.

Traefikin keskeiset ominaisuudet ovat seuraavat:

Automaattinen konfigurointi: Traefik kykenee automaattisesti havaitsemaan uudet kontit tai palvelimet, jotka on liitetty siihen, ja päivittämään reitityksen niiden välillä. Tämä tekee konfiguroinnista joustavaa ja vähentää manuaalista hallintaa.

Dynaaminen reititys: Traefik tarjoaa dynaamisen reitityksen, joka pystyy reitittämään saapuvat pyynnöt oikeille sovelluksille tai palvelimille niiden ominaisuuksien perusteella, kuten URL-polun tai verkkotunnuksen perusteella.

Kuormantasaus: Traefik pystyy tasapainottamaan liikennettä useiden taustalla olevien palvelinten tai konttien välillä. Se jakaa saapuvat pyynnöt tehokkaasti, mikä parantaa sovellusten suorituskykyä ja vähentää yksittäisen palvelimen kuormitusta.

SSL-salaus ja Let's Encrypt -integraatio: Traefik tukee SSL-salausta ja tarjoaa helpon integraation Let's Encrypt -sertifikaattien automaattista hankintaa ja uusimista varten. Näin varmistetaan, että liikenne on salattu ja luotettava.

Traefik on suosittu valinta konttien hallintaan ja sovellusten joustavaan reititykseen. Sen avulla voidaan helposti rakentaa joustavia ja skaalautuvia arkkitehtuureja, joissa kontit ja mikropalvelut toimivat tehokkaasti yhdessä.

## Käyttötarkoitus tässä toteutuksessa
Tässä toteutuksessa Traefikia käytetään enimmäkseen mikropalveluarkkitehtuurivaatimuksen toteutukseen, sillä verkon sisältä ulos palveltavia kohteita ei ole Nginxin lisäksi, jota voisi itseäänkin käyttää tässä käyttötarkoituksessa. Koska tehtävän tarkoitus on kuitenkin osoittaa kontainerisoinnin ja mikropalveluarkkitehtuurin toteutumista, on välityspalvelin valittu toteutettavaksi erillisenä palvleuna.

Traefikin avulla nginx-palvelinkohteet voidaan osoittaa halutun dns-nimen kautta, jona tässä tapauksessa käytetään fbi.com -domainia, joka ohjaa kutsut localhost-kohteisiin.

## Kontin määrittely
Välityspalvelinkontille on määritetty julkaistavaksi portit 8080 ja 80, joista ensimmäistä hyödynnetään Traefikin web-käyttöliittymän hallintaan, ja jälkimmäisen kautta ohjataan kutsuja verkon sisällä sijaitsevaan Nginx-palvleimeen. Kutsut Nginxille ohjataan verkkotunnuksen "myhugo.fbi.com" kautta, joka on määritetty docker-compose.yml:ssä web-palvelimeen labels-määrityksen kautta.
