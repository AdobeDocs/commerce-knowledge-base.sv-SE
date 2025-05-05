---
title: Begäran om förbättrad integreringsmiljö - Pro och Starter
description: Om du är kund hos Adobe Commerce på en Pro-planarkitektur i molnet och för närvarande använder integreringsmiljöer av standardstorlek, eller om du är kund hos Adobe Commerce på en Starter-planarkitektur i molnet och för närvarande använder den standardiserade mellanlagringsmiljön och vill ha mer kraft, kan du begära en uppgradering till förbättrade integreringsmiljöer, som ger ungefär fyra gånger så höga prestanda. I den här artikeln finns olika instruktioner för Pro-kunder och Starter-kunder.
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# Begäran om förbättrad integreringsmiljö - Pro och Starter

Om du är kund hos Adobe Commerce på en Pro-planarkitektur i molnet och för närvarande använder integreringsmiljöer av standardstorlek, eller om du är kund hos Adobe Commerce på en Starter-planarkitektur i molnet och för närvarande använder den standardiserade mellanlagringsmiljön och vill ha mer kraft, kan du begära en uppgradering till förbättrade integreringsmiljöer, som ger ungefär fyra gånger så höga prestanda. I den här artikeln finns olika instruktioner för Pro-kunder och Starter-kunder.

>[!NOTE]
>
> Uppgradering till Förbättrad integrering kanske inte löser alla prestandaproblem eftersom det skulle bero på den totala resurskraven för din installation, inklusive tredjepartsintegreringar eller anpassningar.
>
> Ni måste också se till att ni följer de bästa metoderna för bästa prestanda i integreringsmiljön, och även det kanske inte är en totallösning. Använd följande dokumentation för vägledning: [Pro-arkitektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment) och [Starter-arkitektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment) i Commerce on Cloud Infrastructure Guide.

## Pro

1. Om du använder Pro måste du minska antalet integreringsgrenar till två (**huvudintegreringsgrenen inkluderas i summan**) för att kunna uppgradera. **Obs! Räkna inte med den primära grenen i den här summan. Den primära grenen betraktas inte som en integreringsgren.** Följ stegen i [Hantera grenar med molnkonsolen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) i vår utvecklardokumentation.
1. Handlaren måste [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och begära en uppgradering till förbättrade integreringsmiljöer, med hjälp av kontaktorsaken *Begär en ändring av molnkonfigurationen*.
1. Adobe kundkonstruktionsgrupp bekräftar antalet integreringsmiljöer och påbörjar ändringen.
1. Handlaren meddelas i biljetten när uppgraderingen är klar.
1. Handlaren omdistribuerar integreringsmiljöerna. Följ stegen i [Sammanfoga en gren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) i utvecklardokumentationen. *Obs!* Distributionen sker automatiskt när du kör: <pre>git push-ursprung &lt;branch-name></pre>

Förbättrade prestanda innebär en lyckad uppgradering till förbättrade integreringsmiljöer.

**Anteckningar**:

* Standardstorleken och den förbättrade storleken är de enda två tillgängliga storlekarna.
* Alla integreringsmiljöer för en viss butik har samma storlek - de kan inte storleksändras separat.
* Om du behöver mer än två av de förbättrade integreringsmiljöerna kontaktar du ditt Adobe-kontoteam.

## Starter

1. Starter-planer får inte ha några integreringsgrenar: handlarna måste ta bort integreringsmiljöerna och bara lämna mellanlagringsmiljön. Följ stegen i [Hantera grenar med molnkonsolen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) i vår utvecklardokumentation. Antalet tillgängliga miljöer minskas så att maximalt en integreringsmiljö tillåts.
1. Handlaren måste [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och begära en uppgradering till förbättrade integreringsmiljöer, med hjälp av kontaktorsaken *&quot;Begär en ändring av molnkonfigurationen&quot;* - **din mellanlagringsmiljö är en namngiven integreringsmiljö**.
1. Adobe kundkonstruktionsgrupp bekräftar antalet integreringsmiljöer och påbörjar ändringen.
1. Handlaren meddelas i biljetten när uppgraderingen är klar.
1. Handlaren omdistribuerar integreringsmiljöerna. Följ stegen i [Sammanfoga en gren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) i utvecklardokumentationen. *Obs!* Distributionen sker automatiskt när du kör: <pre>git push-ursprung &lt;branch-name></pre>

Förbättrade prestanda innebär en lyckad uppgradering till förbättrade integreringsmiljöer.

**Anteckningar**:

* Standardstorleken och den förbättrade storleken är de enda två tillgängliga storlekarna.
* Alla integreringsmiljöer för en viss butik har samma storlek - de kan inte storleksändras separat.
* Om du behöver integreringsmiljöer utanför mellanlagring kan du kontakta ditt Adobe-kontoteam.
* Om köpet görs efter den 17 september 2020 kommer den här förbättringen inte att gälla på grund av förstorade integreringsmiljöer.
