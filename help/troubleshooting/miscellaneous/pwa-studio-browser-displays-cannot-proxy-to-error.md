---
title: 'PWA Studio: Webbläsaren visar "Kan inte skriva proxy till"fel"'
description: I det här avsnittet beskrivs en lösning när webbläsaren visar en "*Kan inte användas som proxy till*" och konsolen visar en
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# PWA Studio: Webbläsaren visar felet&quot;Det går inte att skriva proxy till&quot;

I det här avsnittet beskrivs en lösning när webbläsaren visar en *Kan inte proxyserver till* och konsolen visar en

```
ENOTFOUND
```

fel vid användning av Progressive Web App (PWA) Studio för Adobe Commerce.

## Berörda produkter och versioner

* PWA Studio för Adobe Commerce

## Problem

<u>Steg för att återskapa</u>:

* Läs in din Adobe Commerce Store i en webbläsare.

<u>Förväntat resultat</u>:

* Adobe Commerce Store läses in normalt i webbläsaren.

<u>Faktiskt resultat</u>:

* Webbläsaren visar felet *Kan inte proxyservern* och konsolen visar ett fel som:

```
    ENOTFOUND
```


## Orsak

NodeJS kan inte matcha värdnamnet för din Adobe Commerce-butik.

## Lösning

1. Se till att din Adobe Commerce Store läses in i mer än en webbläsare.
1. Om du kör en lokal DNS-server eller VPN lägger du till en post i värdfilen (som finns i `/etc/hosts`) och mappar den här domänen manuellt ([Allmänna instruktioner för redigering av värdfiler](https://linuxize.com/post/how-to-edit-your-hosts-file/)) så att NodeJS kan lösa det.

## Relaterad läsning

* [PWA Studio för Adobe Commerce-dokumentation](https://magento.github.io/pwa-studio/)
* [Verktyg och bibliotek](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
