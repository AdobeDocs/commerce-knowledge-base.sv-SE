---
title: robots.txt ger 404 fel Adobe Commerce i molninfrastrukturen
description: I den här artikeln finns en korrigering för när filen "robots.txt" genererar ett 404-fel i Adobe Commerce i molninfrastrukturen.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt ger 404 fel Adobe Commerce i molninfrastrukturen

I den här artikeln finns en korrigering för när `robots.txt` filen genererar ett 404-fel i Adobe Commerce i molninfrastrukturen.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur (alla versioner)

## Problem

The `robots.txt` filen fungerar inte och genererar ett Nginx-undantag. The `robots.txt` filen genereras dynamiskt &quot;i farten&quot;. The `robots.txt` filen inte är tillgänglig för `/robots.txt` URL eftersom Nginx har en omskrivningsregel som tvingar om alla `/robots.txt` till `/media/robots.txt` som inte finns.

## Orsak

Detta inträffar vanligtvis när Nginx inte är korrekt konfigurerat.

## Lösning

Lösningen är att inaktivera Nginx-regeln som omdirigeras `/robots.txt` till `/media/robots.txt` -fil. Handlare med aktiverad självbetjäning kan göra det själva, och handlare utan självbetjäning måste skapa en supportanmälan.

Om du inte har aktiverat självbetjäning (eller inte vet om det är aktiverat), [skicka en Magento Support-biljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) begära att omdirigeringsregeln Nginx tas bort från `/robots.txt` förfrågningar till `/media/robots.txt`.

Om du har aktiverat självbetjäning kan du uppgradera ECE-Tools till minst 2002.0.12 och ta bort Nginx-omdirigeringsregeln i `.magento.app.yaml` -fil. Du kan referera till [Lägg till webbplatskarta och sökrobotar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) i vår utvecklardokumentation för mer information.

## Relaterad läsning

* [Så här blockerar du skadlig trafik för Magento Commerce Cloud på snabbnivå](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) i vår kunskapsbas för support.
* [Lägg till webbplatskarta och sökrobotar](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) i vår dokumentation för utvecklare.
* [Sökmotorrobotar](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) i vår användarhandbok.
