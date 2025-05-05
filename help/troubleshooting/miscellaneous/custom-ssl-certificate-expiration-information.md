---
title: Information om förfallodatum för anpassat SSL-certifikat
description: Den här artikeln innehåller en lösning för när ett anpassat SSL-certifikat uppdaterades med ett SSL-certifikat som tillhandahålls av Adobe.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Information om förfallodatum för anpassat SSL-certifikat

Den här artikeln innehåller en lösning för när ett anpassat SSL-certifikat uppdaterades med ett SSL-certifikat som tillhandahålls av Adobe.

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

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

Om du befinner dig i en situation där din anpassade SSL har ersatts av vår interna SSL och du vill ersätta den med ditt uppdaterade anpassade SSL-certifikat, [skickar du en supportförfrågan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) till den plats du överförde dina nya certifikatfiler. Ange startdatum för den nya SSL:en. När vi har fått den här informationen kan vi gå vidare med att installera det nya SSL-certifikatet.

## Relaterad läsning

* [SSL-certifikat (TLS) för Magento Commerce Cloud: Frågor och svar](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) i vår kunskapsbas för support.
* [Referens för kommandoradsverktyg: magento-cloud certificate:add](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-reference#certificateadd) i utvecklardokumentationen.
* [Starta checklistan](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/launch/checklist)i utvecklardokumentationen.
* [Använd webbplatsövergripande analysverktyg](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/site-wide-analysis-tool/access#step-2-access-site-wide-analysis-tool) i vår användarhandbok.
