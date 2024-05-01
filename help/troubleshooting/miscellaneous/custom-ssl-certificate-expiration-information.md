---
title: Information om förfallodatum för anpassat SSL-certifikat
description: Den här artikeln innehåller en lösning för när ett anpassat SSL-certifikat uppdaterades med ett SSL-certifikat som tillhandahålls av Adobe.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Information om förfallodatum för anpassat SSL-certifikat

Den här artikeln innehåller en lösning för när ett anpassat SSL-certifikat uppdaterades med ett SSL-certifikat som tillhandahålls av Adobe.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Adobe Commerce uppdaterar automatiskt SSL-certifikat 30 dagar innan de upphör att gälla. Den här automatiseringen kontrollerar inte om det certifikat som ersätts är en intern SSL eller en anpassad SSL från tredje part och ersätter den med en giltig intern SSL när förfallodatum upptäcks. Detta kan skapa förvirring för webbplatsägare och operatörer som förväntar sig att ha det anpassade certifikatet på platsen, samt risken för andra funktionsproblem, inklusive, men inte begränsat till, ett webbplatsutbrott.

<u>Steg som ska återskapas</u>

1. Anpassat SSL-certifikat har installerats för webbplatsen.
1. Automation identifierar att det anpassade SSL-certifikatet är 30 dagar långt ifrån giltigt.
1. Adobe Commerce ersätter automatiskt det anpassade certifikatet med vårt interna certifikat.

<u>Förväntade resultat</u>

Adobe Commerce hoppar över anpassade certifikat när den automatiserade uppdateringen av SSL-certifikat körs.

<u>Faktiska resultat</u>

Adobe Commerce uppdaterar alla certifikat när de är 30 dagar från utgångsdatum.

## Lösning

När en handlare väljer att använda sitt eget anpassade SSL-certifikat måste det uppdateras mer än 30 dagar innan certifikatet upphör att gälla för att säkerställa att det inte ersätts av ett internt Adobe Commerce SSL-certifikat.

Om du befinner dig i en situation där din anpassade SSL har ersatts av vår interna SSL och du vill ersätta den med ditt uppdaterade anpassade SSL-certifikat, ber vi dig [skicka en supportförfrågan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) med den plats där du överförde dina nya certifikatfiler. Ange startdatum för den nya SSL:en. När vi har fått den här informationen kan vi gå vidare med att installera det nya SSL-certifikatet.

## Relaterad läsning

* [SSL-certifikat (TLS) för Magento Commerce Cloud: Frågor och svar](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) i vår kunskapsbas för support.
* [Kommandoradsverktyg, referens: magento-cloud-certifikat:add](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-cloud.html#certificateadd) i vår dokumentation för utvecklare.
* [Öppna checklista](https://devdocs.magento.com/cloud/live/site-launch-checklist.html)i vår dokumentation för utvecklare.
* [Access Site-Wide Analysis Tool](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html#step-2-access-site-wide-analysis-tool) i vår användarhandbok.
