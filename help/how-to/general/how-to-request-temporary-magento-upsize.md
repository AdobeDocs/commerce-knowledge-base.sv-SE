---
title: Hur man begär tillfälliga Adobe Commerce-lösningar för molninfrastruktur
description: Om din organisation planerar en onlinehändelse där du förväntar dig hög trafik, eller om du plötsligt upptäcker att din webbplats håller på att genomgå en stor trafikaktivitet, kan du arkivera en [supportbiljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-tickets) och begära tillfällig ytterligare molnkapacitet för din Adobe Commerce i molninfrastrukturbutiken.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: e59335b67e1f33e138e34cab93ce593836d14b48
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Hur man begär tillfälliga Adobe Commerce-lösningar för molninfrastruktur

Om din organisation planerar en onlinehändelse där du förväntar dig hög trafik, eller om du plötsligt upptäcker att din webbplats håller på att genomgå en stor trafikaktivitet, kan du arkivera en [supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att begära tillfällig ytterligare molnkapacitet för din Adobe Commerce i molninfrastrukturbutiken.

>[!NOTE]
>
>48 arbetstimmar måste varnas för icke-akuta begäranden om storleksanpassning. Uppgraderingar för marknadsföringskampanjer betraktas inte som kriser om webbplatsen inte är helt icke-fungerande eller får mycket högre trafik än förväntat och prestanda har försämrats avsevärt.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Identifiera trafikhändelser

I New Relic Alerts kan du använda baslinjevarningsvillkor för att definiera tröskelvärden som justeras efter databeteendet.

Aviseringar vid baslinjen är användbara när du skapar varningstillstånd som:

* Meddela dig bara när data beter sig onormalt.
* Anpassa dynamiskt till föränderliga data och trender, inklusive trender varje dag eller vecka.

Dessutom fungerar baslinjevarningar bra med nya program när du ännu inte har några kända beteenden.

Följ den här länken om du vill veta mer om New Relic [Anomaly-identifiering med den använda intelligensen](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/).

Om du får ett varningsmeddelande som tyder på en hög trafikhändelse kan du behöva överväga att [skicka en supportanmälan](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) och begära ytterligare kapacitet. Följ stegen nedan.

## Så här övervakar du webbplatsens prestanda

Adobe tillhandahåller en uppsättning av New Relic aviseringspolicyer för Adobe Commerce om molninfrastruktur Pro-planarkitekturen och Adobe Commerce om molninfrastruktur Starter-planens arkitektur Produktionsmiljöer för att spåra följande viktiga prestandamått:

* [API-poäng](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Felfrekvens
* Diskutrymme (endast tillgängligt i Pro-arkitekturens produktionsmiljöer)

De här riktlinjerna bygger på branschens bästa praxis och sätter tröskelvärden för varningar och kritiska förhållanden som påverkar prestandan. När en infrastruktur- eller programsäkerhetslucka som utlöser ett tröskelvärde för avisering inträffar på din webbplats skickar New Relic varningsmeddelanden så att du kan åtgärda problemet proaktivt. Om du vill använda de här profilerna måste du konfigurera meddelandekanaler så att du kan ta emot varningsmeddelanden.

Följ den här länken om du vill lära dig hur du [konfigurerar prestandabaserade aviseringar](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Steg för att begära tillfällig storlek

Om du vill begära tillfällig ytterligare molnkapacitet skickar du en [supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) till Adobe Commerce Support Center med följande information:

>[!NOTE]
>
>Valet *Helgdagsbegäran* är bara ett alternativ mellan oktober- och december-månaderna.

1. Välj den [!DNL Adobe Commerce]-produkt som du behöver support för:
   * [!DNL Commerce Cloud]
   * [!DNL Commerce on Managed Service]

1. Ange följande fält:
   * **[!UICONTROL Case Title]**
   * **[!UICONTROL Case Description]** *(se till att dessa tydligt beskriver problemet och sammanhanget.)*

1. Välj *Begäran om infrastrukturändring* i listrutan **[!UICONTROL Issue Reason]**.

1. Välj **[!UICONTROL Environment]** i listrutan.

1. Välj lämplig **[!UICONTROL Product Version]** i listrutan.

1. Välj *Storleksändring för molnprojekt (vCPU)* i listrutan **[!UICONTROL Which Infra Change you would like to do today]**.

1. **Välj[!UICONTROL Architecture]**:
   * *Standardarkitektur:* Välj *Nästa tillgängliga storlek* i listrutan **Välj storlek**.
   * *Skalad arkitektur:* När du väljer det här alternativet ändras skärmen till två ytterligare fält:
      * *Storlek för webbnod*
      * *Storlek för servicenod* *(ange önskad storlek för varje nod.)*

1. Ange **[!UICONTROL From Date]** i UTC-format (datum och tid).

1. Ange **[!UICONTROL To Date]** i UTC-format (datum och tid).

1. Ange **[!UICONTROL Project URL]** *(finns under https://accounts.magento.cloud/, vanligtvis i formatet `https://[REGION].magento.cloud/projects/PROJECT_ID`)*

1. Ange **[!UICONTROL Project ID]**.

1. Ange **[!UICONTROL Affected URL]** *(måste börja med `http://` eller `https://`.)*

1. Välj **[!UICONTROL Priority]**.

1. Välj **[!UICONTROL Business Impact]**.

1. Bekräfta **[!UICONTROL Time Zone]** *(t.ex. `(UTC-5:00) Indiana (East)`)*

1. Ange **[!UICONTROL Phone Number]** *(t.ex. `+12015550123`)*

1. Klicka på **[!UICONTROL Submit]** för att slutföra ditt supportärende.

>[!NOTE]
>
>När storleken är schemalagd justeras storleken på molninstansen av ett automatiskt system. Du får inte få någon anmälan om biljett när proceduren är klar. Du kan använda verktyget Observation for Adobe Commerce för att visa dina AWS- eller Azure-instanstyper för att [verifiera ändringen](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## Visa historiken för dina uppgraderingar

Du kan visa historiken för begärda storlekar genom att begära information från din **CSM (Customer Success Manager)**.
Följande information finns för varje begäran om storleksändring:

* **Storlek på startdatum**: datum för begäran om uppstorleksändring.
* **Slutdatum för storleksändring**: det datum då klustret återgick till den tidigare storleken.
* **vCPU-storlek**: storleken på klustret efter storleken.
* **Dagar för användning**: under hur många dagar som klustret förblev uppskalat.
* **Period vCPU**: vCPU-storleken har ändrats med antalet dagar som den användes. (till exempel är vCPU-storleken 192 x 25 dagar lika med 4 800).


## Relaterad läsning

* Information, metoder och exempel på hur du mäter och förbättrar webbplatsens prestanda finns i följande ingående artiklar i vår kunskapsbas för support:
   * [CPU allokeringsberäkning för Adobe Commerce i molnet](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Kontrollera om det krävs en uppstorlek för värdinstanserna för Adobe Commerce i molnet](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [Kontrollera värddatorns CPU-konfiguration för Adobe Commerce i molnet](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Mer information om hur du identifierar avbrott finns i [Identifiera och mäta avbrott för Adobe Commerce i molnet](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) i vår kunskapsbas för support.
* Mer information om hur du förbättrar webbplatsens prestanda för att undvika behovet av att utnyttja en kapacitetsökning finns i följande artiklar i vår utvecklardokumentation:
   * [Bildstorlek](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [Cachelagring av hela sidor](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-verktyg](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
