---
title: robots.txt ger 404 fel Adobe Commerce i molninfrastrukturen
description: I den här artikeln finns en korrigering för när filen "robots.txt" genererar ett 404-fel i Adobe Commerce i molninfrastrukturen.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt ger 404 fel Adobe Commerce i molninfrastrukturen

Den här artikeln innehåller en korrigering för när filen `robots.txt` genererar ett 404-fel i Adobe Commerce i molninfrastrukturen.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur (alla versioner)

## Problem

Filen `robots.txt` fungerar inte och genererar ett Nginx-undantag. Filen `robots.txt` genereras dynamiskt &quot;i farten&quot;. `robots.txt`-filen är inte tillgänglig av URL:en `/robots.txt` eftersom Nginx har en omskrivningsregel som tvingar alla `/robots.txt`-begäranden till `/media/robots.txt`-filen som inte finns.

## Orsak

Detta inträffar vanligtvis när Nginx inte är korrekt konfigurerat.

## Lösning

Lösningen är att inaktivera Nginx-regeln som omdirigerar `/robots.txt`-begäranden till `/media/robots.txt`-filen. Handlare med aktiverad självbetjäning kan göra det själva, och handlare utan självbetjäning måste skapa en supportanmälan.

Om du inte har aktiverat självbetjäning (eller inte vet om det är aktiverat) [skickar du en Magento-supportbiljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och begär att Nginx-omdirigeringsregeln ska tas bort från `/robots.txt`-begäranden till `/media/robots.txt`.

Om du har aktiverat självbetjäning kan du uppgradera ECE-Tools till minst 2002.0.12 och ta bort Nginx-omdirigeringsregeln i filen `.magento.app.yaml`. Mer information finns i [Lägg till webbplatskarta och sökrobotar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html?lang=sv-SE) i utvecklardokumentationen.

## Relaterad läsning

* [Så här blockerar du skadlig trafik för Magento Commerce Cloud på snabbnivå](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) i vår kunskapsbas för support.
* [Lägg till webbplatskarta och sökrobotar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) i utvecklardokumentationen.
* [Sökmotorrobotar](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html?lang=sv-SE#search-engine-robots) i användarhandboken.
