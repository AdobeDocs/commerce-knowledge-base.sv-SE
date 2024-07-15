---
title: Faktablad för övervakning av  [!DNL Adobe Commerce on cloud pro infrastructure]
description: Det här dokumentet innehåller information om övervakning och meddelanden av Adobe Commerce infrastruktur.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 4926bcff19b8c4c7e2a9a9dfb0cb1fc72a9821ba
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Faktablad för övervakning av [!DNL Adobe Commerce on cloud pro infrastructure]

Det här dokumentet innehåller information om övervakning och meddelanden av Adobe Commerce infrastruktur.

Övervakning gör det möjligt för handlare, systemintegratörer och interna Adobe-team att felsöka webbplatsens tillgänglighet och otillräckligt diskutrymme.

## Felsökning och lösning av problem

Adobe Commerce-instanser innehåller vanligtvis anpassad kod och konfigurationer. Adobe stöder inte eller löser problem med anpassad kod och konfigurationer. Adobe hjälper handlare att felsöka och identifiera problem i vår kunskapsbas och tillhandahåller rekommenderade lösningar och bästa praxis för förebyggande och lösning. Vi uppmuntrar handlare och partners att använda tabellerna nedan för att förstå vad som övervakas och vem som ansvarar för lösningen.

När meddelanden utlöses kommer Adobe Commerce supportteam att lösa problemet. Som en del av triaget analyseras felloggar och andra resurser. Baserat på resan skapas ytterligare [!DNL Zendesk] supportärenden antingen till handlare eller partners (vid anpassade uppdateringar) eller till interna Adobe-team för att lösa problemet.

## Adobe Commerce: standardövervakning

Evenemangen nedan övervakas och Adobe Commerce team vidtar de åtgärder som krävs för att lösa och informera om identifierade problem.

## Övervakning av webbplatstillgänglighet

| Platstillgänglighet | Beskrivning |
|------------|------------|
| **Övervakningsmål** | För att spåra webbplatsens tillgänglighet. |
| **Instrumenterad** | Enskild [!DNL URL] har valts för hög [!DNL SLA]. |
| **Beskrivning** | Platsens tillgänglighet bestäms utifrån de tröskelvärden som konfigurerats runt måttet. Meddelande om driftstopp på webbplatsen utlöses om kontrollen misslyckas i 10 minuter och det inte pågår någon aktiv distribution. |
| **Meddelandemottagare** | Merchant/Partner och Adobe. |
| **Åtgärd av Adobe** | Ansvarig för att testa och åtgärda problem i Adobe Commerce infrastruktur. |
| **Handling av handlare** | Ansvarig för att åtgärda problemet om det orsakas av ändringar eller anpassad kod som införts av handlaren/partnern. Felsökning finns i: [Felsökning av webbplats](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html). |

## Övervakning av diskutrymme

| Övervakning av diskutrymme | Beskrivning |
|------------|------------|
| **Övervakningsmål** | För att spåra diskutrymmesanvändning. |
| **Instrumenterad** | [!DNL MySQL] disk- och mediediskpartitioner. |
| **Mått** | Ledigt diskutrymme övervakas varje minut på värden. Varningen visas om bara 5 % eller 2 GB ledigt utrymme finns kvar. Det kritiska tröskelvärdet för återstående ledigt utrymme är 2 % eller 1 GB. |
| **Beskrivning** | Meddelandet skickas baserat på tröskelvärdena som konfigurerats runt ledigt diskutrymme för värden. Ytterligare diskutrymme läggs automatiskt till en gång till relevant plats ([!DNL MySQL] eller media) för att förhindra ett driftstopp på en webbplats och för att ge handlaren tid att frigöra diskutrymme och/eller identifiera och lösa kod eller loggar som kan öka diskanvändningen. |
| **Meddelandemottagare** | Merchant/Partner och Adobe. |
| **Åtgärd av Adobe** | Öka supportbiljetten automatiskt och ytterligare diskutrymme läggs automatiskt till i den relevanta monteringen ([!DNL MySQL] eller media) för att förhindra att en webbplats går sönder. |
| **Handling av handlare** | Om du vill få varningar om diskutrymme på varningsnivå kan du läsa: <ul><li>[[!DNL Managed alerts for Adobe Commerce]: skivvarning](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-warning-alert.html)</li><li>[[!DNL Managed alerts for Adobe Commerce]: Diskkritisk varning](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-critical-alert.html) </li></ul> |
