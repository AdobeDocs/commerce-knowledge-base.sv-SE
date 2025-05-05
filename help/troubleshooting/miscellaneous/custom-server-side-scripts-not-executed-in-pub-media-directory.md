---
title: Anpassade serverskript körs inte i pub-mediekatalogen
description: I den här artikeln finns en korrigering för när anpassade serverskript inte körs om de placeras i &grave;./pub/media/" för ditt Adobe Commerce-program i molninfrastrukturen. Detta är en förväntad säkerhetsbegränsning, eftersom &grave;.Katalogen /pub/media/&grave; är skrivbar. Om du vill göra skript körbara placerar du dem i kataloger som inte är skrivbara, till exempel &grave;./app/code/&grave; eller &grave;./pub/&grave;.
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

* [Cloud för Adobe Commerce > Projektstruktur > Skrivbara kataloger](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/project/file-structure#writable-directories) i vår utvecklardokumentation.
