---
title: Stock-bilder visas inte, Adobe Commerce och Magento Open Source 2.3.7-p2
description: I den här artikeln finns en lösning på problemet där Adobe stockbilder som överförts till filsystemskatalogerna "pub/media" eller "pub/media/catalog" inte visas i användargränssnittet för mediegalleriet. Detta beror på att bilderna ligger utanför de tillåtna mediegallerikatalogerna. För att de här bilderna ska kunna visa handlare måste du ta bort bilderna i filsystemet och överföra dem till en tillåten Media Gallery-katalog igen.
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Stock-bilder visas inte, Adobe Commerce och Magento Open Source 2.3.7-p2

I den här artikeln finns en lösning på problemet med att stockbilder i Adobe överfördes till filsystemkatalogerna `pub/media` eller `pub/media/catalog` visas inte i användargränssnittet för mediegalleriet. Detta beror på att bilderna ligger utanför de tillåtna mediegallerikatalogerna. För att de här bilderna ska kunna visa handlare måste du ta bort bilderna i filsystemet och överföra dem till en tillåten Media Gallery-katalog igen.

## Berörda produkter och versioner

* Adobe Commerce och Magento Open Source 2.3.7-p2


## Problem

Handlare kan överföra Adobe Stock-bilder till lagringsroten i mediegalleriet, men dessa bilder visas inte i användargränssnittet och kommer att se ut som om de inte hade överförts. Detta beror på att systemet meddelar att bilden redan har överförts till filsystemet, även om den inte är tillgänglig i användargränssnittet för mediegalleriet. Det innebär att när en handlare överför en bild till `pub/media` eller `pub/media/catalog`kan de inte använda den bilden förrän den tas bort direkt i filsystemet.

<u>Steg som ska återskapas</u>

1. Aktivera Adobe Stock med giltiga API-nycklar.
1. Öppna mediegalleri (**Katalog** > **Kategorier** > **Innehåll** sektion > klicka **Välj från galleri**).
1. Klicka **Sök i Adobe Stock**.
1. Markera en bild. Klicka **Spara förhandsgranskning**. Observera att du kanske måste återställa stödrastret för Adobe Stock för att bilderna ska visas.

<u>Förväntat resultat</u>:

Bilden visas.

<u>Faktiskt resultat</u>:

Ett felmeddelande visas: *Det går inte att hitta bilden. Det går inte att hitta den här bilden i mediegalleriet.*

## Orsak

Du kan överföra bilder till lagringsroten för mediegalleriet via Adobe Stock.

## Lösning

Välj valfri underkatalog till lagringsroten för mediegalleriet (utom **Lagringsrot** > **Katalog**) innan du överför en Adobe Stock-bild.
Ta bort överförda Adobe Stock-bilder från `pub/media` och `pub/media/catalog` mappar i Adobe Commerce filsystem och överför bilder till tillåtna Media Gallery Storage Root-underkataloger istället (förutom **Lagringsrot** > **Katalog**).

## Relaterad läsning

* [Medielagring](https://docs.magento.com/user-guide/v2.3/cms/media-storage.html) i vår användarhandbok.
