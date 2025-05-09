---
title: robots.txt har inte uppdaterats eller standardinställningar visas
description: Artikeln innehåller en lösning för när du har konfigurerat "robots.txt" korrekt, till exempel enligt [Best practices for Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) men "robots.txt" uppdateras inte eller visar standardinställningarna.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt har inte uppdaterats eller standardinställningar visas

Artikeln innehåller en lösning för när du har konfigurerat `robots.txt` korrekt, till exempel enligt [Bästa praxis för Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), men `robots.txt` uppdateras inte eller visar standardinställningarna.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.3.x, 2.4.x

## Problem

Det går inte att ändra standardinställningen för `robots.txt`.

<u>Steg att återskapa:</u>

1. Öppna panelen Admin.
1. Lägg till innehåll i **Innehåll** > Design > **Konfiguration** > **Redigera anpassad instruktion för filen`robots.txt`**, till exempel texten &quot;hello&quot;, och spara ändringarna.
1. Besök `robots.txt`-URL:en.

<u>Förväntat resultat:</u>
`robots.txt` innehåller den sparade texten.

<u>Faktiskt resultat:</u>

Filen `robots.txt` ändras inte.

## Orsak

Indexering med sökmotorer är inaktiverat.

## Lösning

Aktivera indexering av sökmotorer. Se [Konfigurera indexering med hjälp av sökmotor](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap#configure-indexing-by-search-engine) i utvecklardokumentationen.

## Relaterad läsning

* [Lägg till webbplatskarta och sökrobotar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) i utvecklardokumentationen.
