---
title: Hämtningen misslyckas på grund av ändringar i Composer
description: I den här artikeln finns en korrigering för ett fel med hämtning och undantag från Adobe Commerce.
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Hämtningen misslyckas på grund av ändringar i Composer

I den här artikeln finns en korrigering för ett fel med hämtning och undantag från Adobe Commerce.

## Problem

Under hämtningen visas följande fel:

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Orsak

Detta beror på ändringar i vissa versioner av Composer. Du kan kringgå problemet genom att nedgradera Composer till en tidigare version och försöka hämta Adobe Commerce igen.

## Lösning

Alla versioner av Composer som är daterade mellan 21 november och 26 november 2015 har detta problem. Bekräfta att problemet är relaterat till Composer-versionen genom att ange följande kommando:

```php
composer -v
```

Versionen ser ut ungefär så här:

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

Observera att datumet är 2015-11-25, vilket anger att det är något problem med Composer.

Så här undviker du det:

1. Ändra din version av Composer så att du kan hämta Adobe Commerce-programmet genom att göra något av följande:

   * Nedgradera disposition med följande kommando: `composer self-update 1.0.0-alpha11`.
   * Uppgradera disposition till en version som är senare än 26 november 2015: `composer self-update`.

1. Ta bort din Adobe Commerce-katalog och underkataloger.
1. Försök hämta igen med antingen `[composer create-project](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/composer)` eller `[git clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)`.
1. Uppdatera disposition: `composer self-update` när du har hämtat Adobe Commerce-programmet.
