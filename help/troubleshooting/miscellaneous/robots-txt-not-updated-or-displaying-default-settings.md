---
title: robots.txt har inte uppdaterats eller standardinställningar visas
description: Artikeln innehåller en lösning för när du har konfigurerat "robots.txt" korrekt, till exempel enligt [Best practices for Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) men "robots.txt" uppdateras inte eller visar standardinställningarna.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt har inte uppdaterats eller standardinställningar visas

Artikeln innehåller en lösning för när du har konfigurerat `robots.txt` korrekt, till exempel per [Bästa tillvägagångssätt för Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) men `robots.txt` uppdateras inte eller visar standardinställningarna.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.3.x, 2.4.x

## Problem

Det går inte att ändra standardinställningen `robots.txt` inställning.

<u>Steg som ska återskapas:</u>

1. Öppna panelen Admin.
1. Lägg till innehåll i **Innehåll** > Design > **Konfiguration** > **Redigera anpassad instruktion för`robots.txt`** som texten &quot;hello&quot; och spara ändringarna.
1. Besök `robots.txt` url.

<u>Förväntat resultat:</u>
`robots.txt` har den sparade texten.

<u>Faktiskt resultat:</u>

`robots.txt` filen ändras inte.

## Orsak

Indexering med sökmotorer är inaktiverat.

## Lösning

Aktivera indexering av sökmotorer. Se [Konfigurera indexering med sökmotor](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html#configure-indexing-by-search-engine) i vår dokumentation för utvecklare.

## Relaterad läsning

* [Lägg till webbplatskarta och sökrobotar](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) i vår dokumentation för utvecklare.
