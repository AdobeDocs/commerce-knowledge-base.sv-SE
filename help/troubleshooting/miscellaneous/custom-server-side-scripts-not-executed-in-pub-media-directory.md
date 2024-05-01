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

I den här artikeln finns en fix för när anpassade serverskript inte körs om de placeras i `./pub/media/` katalogen för ditt Adobe Commerce-program i molninfrastrukturen. Detta är en förväntad säkerhetsbegränsning eftersom `./pub/media/` katalogen är skrivbar. Om du vill göra skript körbara placerar du dem i kataloger som inte är skrivbara, till exempel `./app/code/` eller `./pub/`.

## Berörda versioner

* Adobe Commerce i molninfrastruktur: 2.1.x och senare, arkitektur för Starter- och Pro-planer, Wings- och Legacy-arkitekturer

## Utgåva: skript körs inte

Anpassade skript på serversidan kan inte köras när de initieras.

När slutanvändaren (Adobe Commerce-kund) till exempel klickar på länken som leder till `\*.php` fil med skriptet (som *domain.com/media/directory/script.php* ) laddas skriptet ned i stället för att köras.

## Orsak: felaktig plats för skriptfilen

Problemet inträffar när skriptfilerna finns i `./pub/media/` katalog för Adobe Commerce-program i molninfrastruktur. Detta är ett förväntat beteende: på grund av säkerhetsbegränsningar kan filer från skrivbara kataloger (`./pub/media/`) verkställs aldrig.

## Lösning: placera skript i kataloger som inte är skrivbara

Lagra serverskript i kataloger som inte kan skrivas, t.ex. `./app/code/` eller `./pub/`  &quot;

## Relaterad dokumentation

* [Cloud for Adobe Commerce > Projektstruktur > Skrivbara kataloger](https://devdocs.magento.com/guides/v2.3/cloud/project/project-start.html#write-dir) i vår dokumentation för utvecklare.
