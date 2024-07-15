---
title: Anpassade serverskript körs inte i pub-mediekatalogen
description: I den här artikeln finns en korrigering för när anpassade serverskript inte körs om de placeras i `./pub/media/" för ditt Adobe Commerce-program i molninfrastrukturen. Detta är en förväntad säkerhetsbegränsning, eftersom `.Katalogen /pub/media/` är skrivbar. Om du vill göra skript körbara placerar du dem i kataloger som inte är skrivbara, till exempel `./app/code/` eller `./pub/`.
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Anpassade serverskript körs inte i pub-mediekatalogen

Den här artikeln innehåller en korrigering för när anpassade serverskript inte körs om de placeras i katalogen `./pub/media/` i ditt Adobe Commerce-program i molninfrastrukturen. Det här är en förväntad säkerhetsbegränsning eftersom katalogen `./pub/media/` är skrivbar. Om du vill göra skript körbara placerar du dem i kataloger som inte är skrivbara, till exempel `./app/code/` eller `./pub/`.

## Berörda versioner

* Adobe Commerce i molninfrastruktur: 2.1.x och senare, arkitektur för Starter- och Pro-planer, Wings- och Legacy-arkitekturer

## Utgåva: skript körs inte

Anpassade skript på serversidan kan inte köras när de initieras.

När slutanvändaren (Adobe Commerce shopper) till exempel klickar på länken som leder till filen `\*.php` med skriptet (till exempel *domain.com/media/directory/script.php* ) hämtas skriptet i stället för att köras.

## Orsak: felaktig plats för skriptfilen

Problemet inträffar när skriptfilerna finns i katalogen `./pub/media/` för Adobe Commerce-programmet i molninfrastrukturen. Detta är ett förväntat beteende: på grund av säkerhetsbegränsningar körs aldrig filer från de skrivbara katalogerna (`./pub/media/`).

## Lösning: placera skript i kataloger som inte är skrivbara

Lagra serverskript i kataloger som inte är skrivbara, till exempel `./app/code/` eller `./pub/`

## Relaterad dokumentation

* [Cloud för Adobe Commerce > Projektstruktur > Skrivbara kataloger](https://devdocs.magento.com/guides/v2.3/cloud/project/project-start.html#write-dir) i vår utvecklardokumentation.
