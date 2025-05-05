---
title: Stock-bilder visas inte, Adobe Commerce och Magento Open Source 2.3.7-p2
description: I den här artikeln finns en lösning på problemet där Adobe stockbilder som överförts till filsystemskatalogerna "pub/media" eller "pub/media/catalog" inte visas i användargränssnittet för mediegalleriet. Detta beror på att bilderna ligger utanför de tillåtna mediegallerikatalogerna. För att de här bilderna ska kunna visa handlare måste du ta bort bilderna i filsystemet och överföra dem till en tillåten Media Gallery-katalog igen.
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Stock-bilder visas inte, Adobe Commerce och Magento Open Source 2.3.7-p2

Den här artikeln innehåller en lösning på problemet där stockbilder i Adobe som överförts till filsystemskatalogerna `pub/media` eller `pub/media/catalog` inte visas i användargränssnittet för mediegalleriet. Detta beror på att bilderna ligger utanför de tillåtna mediegallerikatalogerna. För att de här bilderna ska kunna visa handlare måste du ta bort bilderna i filsystemet och överföra dem till en tillåten Media Gallery-katalog igen.

## Berörda produkter och versioner

* Adobe Commerce och Magento Open Source 2.3.7-p2


## Problem

Handlare kan överföra Adobe Stock-bilder till lagringsroten i mediegalleriet, men dessa bilder visas inte i användargränssnittet och kommer att se ut som om de inte hade överförts. Detta beror på att systemet meddelar att bilden redan har överförts till filsystemet, även om den inte är tillgänglig i användargränssnittet för mediegalleriet. Det innebär att när en handlare har överfört en bild till `pub/media` eller `pub/media/catalog` kan de inte använda den bilden förrän den har tagits bort direkt i filsystemet.

<u>Steg som ska återskapas</u>

1. Aktivera Adobe Stock med giltiga API-nycklar.
1. Öppna mediegalleriet (**Katalog** > **Kategorier** > avsnittet **Innehåll** > klicka på **Välj från galleri**).
1. Klicka på **Sök i Adobe Stock**.
1. Markera en bild. Klicka på **Spara förhandsvisning**. Observera att du kanske måste återställa stödrastret för Adobe Stock för att bilderna ska visas.

<u>Förväntat resultat</u>:

Bilden visas.

<u>Faktiskt resultat</u>:

Ett felmeddelande visas: *Det går inte att hitta bilden. Det går inte att hitta den här bilden i mediegalleriet.*

## Orsak

Du kan överföra bilder till lagringsroten för mediegalleriet via Adobe Stock.

## Lösning

Markera en underkatalog i lagringsroten för mediegalleriet (exklusive **lagringsrot** > **katalog**) innan du överför en Adobe Stock-avbildning.
Ta bort överförda Adobe Stock-bilder från mapparna `pub/media` och `pub/media/catalog` i Adobe Commerce filsystem och överför bilder till tillåtna underkataloger i Lagringsrot för mediegalleriet i stället (exklusive **Lagringsrot** > **Katalog**).

## Relaterad läsning

* [Medielagring](https://experienceleague.adobe.com/sv/docs/commerce-admin/content-design/wysiwyg/storage/media-storage) i användarhandboken.
