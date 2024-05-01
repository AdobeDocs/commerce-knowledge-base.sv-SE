---
title: Byt till OpenSearch för Adobe Commerce i molnet 2.4.4
promoted: true
description: Adobe Commerce i molninfrastruktur 2.4.4 stöder inte versioner av Elasticsearch efter 7.10. **Du måste uppgradera till Adobe Commerce 2.4.4 först och sedan omedelbart växla från Elasticsearch till OpenSearch 1.2.x.** Adobe ger detaljerade anvisningar närmare Adobe Commerce 2.4.4 GA-versionen.
exl-id: 0cb34cee-d4d9-428e-a7fd-7301a86dd8f6
feature: Cloud, Iaas, Paas, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Byt till OpenSearch för Adobe Commerce i molnet 2.4.4

Adobe Commerce i molninfrastruktur 2.4.4 stöder inte versioner av Elasticsearch efter 7.10. **Du måste uppgradera till Adobe Commerce 2.4.4 först och sedan omedelbart växla från Elasticsearch till OpenSearch 1.2.x.** Adobe kommer att ge detaljerade anvisningar närmare Adobe Commerce version 2.4.4 GA.

>[!NOTE]
>
>Bytet bör göras oavsett molnleverantör.

Adobe Commerce på plats lägger till stöd för Elasticsearch 7.16 och OpenSearch 1.2 i alla depotappar från mars 2022 (2.4.4, 2.4.3-p2 och 2.3.7-p3). I 2.4.4 kommer Adobe Commerce i molninfrastruktur att gå över till OpenSearch som standardsökmotor, så handlarna måste använda OpenSearch istället för Elasticsearch innan de uppgraderar till Adobe Commerce 2.4.4 eller senare. Handlare med Adobe Commerce lokala distributioner kan använda Elasticsearch eller OpenSearch eftersom Adobe Commerce fortsätter att ha stöd för båda.


## Vad är OpenSearch?

OpenSearch är en gaffel från Elasticsearch och Kibana. Den underhålls av AWS i stället för Elastic.co. Mer information finns i GitHub [opensearch-project/OpenSearch](https://github.com/opensearch-project/OpenSearch).

**Kompatibilitet mellan olika versioner:**

**Kommer Adobe Commerce i molninfrastruktur att stödja Elasticsearch 7.10?**

**Ja** - Från och med mitten av januari 2022 har Adobe Commerce i molninfrastrukturversionerna 2.4.3-p1, 2.4.3-p2 och 2.3.7-p3 stöd för Elasticsearch 7.10.

För Adobe Commerce lokalt rekommenderar vi den senaste 7.16.x-versionen för att minska risken för Log4j.

## Migrering:

## När kan handlare migrera till OpenSearch?

Efter Adobe Commerce 2.4.4.

Innan uppgraderingsprocessen till Adobe Commerce 2.4.4 påbörjas måste dock handlarna ha en aktuell version av Adobe Commerce som stöder Elasticsearch 7.10 och vara på minst Elasticsearch innan uppgraderingsprocessen till Adobe Commerce 2.4.4 eller till OpenSearch påbörjas.

## Vad kan handlare (Adobe Commerce i molninfrastruktur och Adobe Commerce lokalt) som inte befinner sig i 2.4.4 göra? Kan de uppgradera till en version av Elasticsearch som stöds (7.10, 7.16.1) eller till OpenSearch? Måste de ha den senaste versionen som stöds för att göra det (som 2.4.3-p1, 2.3.7-p2, 2.4.3-p1)?

Om Adobe Commerce grundversion har stöd för Elasticsearch 7.10 kan de använda det.

Granska [Systemkrav](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) i vår dokumentation för utvecklare om versionskompatibilitet.

>[!NOTE]
>
>Vi rekommenderar att du uppgraderar till Adobe Commerce 2.4.4 så snart som möjligt eftersom Elasticsearch 7.10 kommer att vara EOL i maj 2022.

Adobe partners kan registrera sig för vårt betatestprogram [här](https://experienceleague.adobe.com/docs/commerce-operations/release/beta-program.html) för att få tillgång till vår senaste beta4-kod som har testats mot Elasticsearch 7.16.1 och OpenSearch 1.1.
