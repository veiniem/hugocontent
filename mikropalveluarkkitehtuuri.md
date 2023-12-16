+++
title = 'Mikropalveluarkkitehtuuri'
date = 2023-12-16T17:12:+02:00
draft = false
+++

# Mikropalveluarkkitehtuuri

Toteutetun ympäristön mikropalveluarkkitehtuuri koostuu kolmesta yksittäistä toimintoa suorittavasta komponentista:
- _Hugo CMS_: Hugo CMS on nopea ja yksinkertainen avoimen lähdekoodin ratkaisu staattisten verkkosivujen luontiin. Hugo käyttää Markdownia sisällön luomiseen ja kääntää staattisen sisällön verkkoformaattiin.
- _Nginx_: Nginx-webpalvelinta käytetään ympäristössä Hugo CMS:n tuottamien staattisten kohteiden tarjoamiseen (serve) verkon yli.
- _Traefik_: Traefik toimii ympäristössä reverse-proxynä piilottaen ympäristön muut kohteet sen ulkopuolelta, ja tarjoten mahdollisuuden liikenteen ja toimintojen monitorointiin.
