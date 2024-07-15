---
title: laminas/laminas-escape 2.7.1 orsakar fel på sidorna Adobe Commerce FrontTand och Admin
description: Den här artikeln innehåller en lösning på problemet där Adobe Commerce funktioner för produkthantering, kategorier och produktsidor inte längre fungerar när man släpper laminas/laminas-escape:2.7.1. Problemet åtgärdas i Adobe Commerce 2.4.3.
exl-id: 89de6827-7b90-4f08-92fb-56ed31ae2672
feature: Admin Workspace, Categories
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# laminas/laminas-escape 2.7.1 orsakar fel på sidorna Adobe Commerce FrontTand och Admin


## Berörda produkter och versioner

* Adobe Commerce på vår Cloud Architecture 2.3.5+
* Adobe Commerce 2.3.5+

## Problem

Efter uppdateringen av laminas/laminas-escape:2.7.1 visas ett felmeddelande på sidan.

<u>Steg som ska återskapas</u>:

Uppdatera laminas/laminas-escape till 2.7.1.

<u>Förväntat resultat</u>:

Inget fel.

<u>Faktiskt resultat</u>:

Efter uppdatering till laminas/laminas-escape:2.7.1 visas ett felmeddelande på en produktredigeringssida (eller produkthanteringssida): *TypeError: rawurlencode() förväntar att parameter 1 ska vara en sträng, int anges i /var/www/magento/vendor/laminas/laminas-escaper/src/Escaper.php:246*
Det här felet inträffar på förgrunds- och administratörssidorna och gör att sidans innehåll förvrängs.

## Orsak

laminas/laminas-escape 2.7.1 började använda strikt typvalidering för klassen Escaper.

## Lösning

Kör `composer require laminas/laminas-escaper:2.7.0` i rotkatalogen för varje projekt.

## Relaterad läsning

laminas-dokumentation: [laminas-escape](https://docs.laminas.dev/laminas-escaper/)
