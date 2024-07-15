---
title: Hur man begär tillfälliga Adobe Commerce-lösningar för molninfrastruktur
description: Om din organisation planerar en onlinehändelse där du förväntar dig hög trafik, eller om du plötsligt upptäcker att din webbplats håller på att genomgå en stor trafikaktivitet, kan du arkivera en [supportbiljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-tickets) och begära tillfällig ytterligare molnkapacitet för din Adobe Commerce i molninfrastrukturbutiken.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: 357e0acb1c849079ff0fe9f53fe386f60475c7f9
workflow-type: tm+mt
source-wordcount: '898'
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

Adobe tillhandahåller en uppsättning New Relic aviseringspolicyer för Adobe Commerce om molninfrastruktur Pro-planarkitekturen och Adobe Commerce om molninfrastruktur Starter-planens arkitektur Produktionsmiljöer för att spåra följande viktiga prestandamått:

* [API-poäng](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Felfrekvens
* Diskutrymme (endast tillgängligt i Pro-arkitekturens produktionsmiljöer)

De här riktlinjerna bygger på branschens bästa praxis och sätter tröskelvärden för varningar och kritiska förhållanden som påverkar prestandan. När en infrastruktur- eller programsäkerhetslucka som utlöser ett tröskelvärde för avisering inträffar på din webbplats skickar New Relic varningsmeddelanden så att du kan åtgärda problemet proaktivt. Om du vill använda de här profilerna måste du konfigurera meddelandekanaler så att du kan ta emot varningsmeddelanden.

Följ den här länken om du vill lära dig hur du [konfigurerar prestandabaserade aviseringar](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Steg för att begära tillfällig storlek

Följ stegen nedan för att skicka en [supportanmälan](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) för att begära tillfällig ytterligare molnkapacitet:

Skicka en [supportanmälan till Adobe Commerce Support Center](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) efter att du har angett följande information:

>[!NOTE]
>
>Valet *Helgdagsbegäran* är bara ett alternativ mellan oktober- och december-månaderna.

1. Välj den Adobe Commerce-produkt som du vill ha support för.
1. Fyll i de fyra första fälten (Produkt, Organisation, Implementeringstyp, Ämne).
1. Välj *Adobe Commerce molninfrastruktur* i listrutan **Kontaktorsak**.
1. Välj *Begäran om överkapacitet för helgdag* i listrutan **Kontaktorsak till Adobe Commerce-infrastruktur** . Klicka på **OK** i popup-meddelandet med en begäran om 48 arbetstimmar för tillfälliga ytterligare begäranden om molnkapacitet.
1. Välj datum för de obligatoriska fälten **Ändra storlek på startdatum** och **Ändra storlek på slutdatum**. Det önskade **Ändra storlek på starttid** är också ett obligatoriskt fält.
1. Fyll i de följande fyra fälten.
1. Om du har ytterligare information om storlek i fältet **Beskrivning** anger du den här. Om ingen specifik större storlek begärs kommer du att uppgraderas till nästa större kapacitet för miljön. Överstrålningsbegäranden får som standard nästa större storlek från den aktuella storleken. Om du behöver ytterligare kapacitet anger du det i fältet **Beskrivning**. Ökad kapacitet dras av från dina avtalade tilläggsdagar eller vCPU-dagar. Det typiska fönstret för kapacitetsökning är fem dagar, men om du behöver fler eller färre dagar anger du detta i din [supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

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
   * [Beräkning av processorallokering för Adobe Commerce i molnet](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Kontrollera om det krävs en uppstorlek för värdinstanserna för Adobe Commerce i molnet](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [Kontrollera värddatorns CPU-konfiguration för Adobe Commerce i molnet](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Mer information om hur du identifierar avbrott finns i [Identifiera och mäta avbrott för Adobe Commerce i molnet](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) i vår kunskapsbas för support.
* Mer information om hur du förbättrar webbplatsens prestanda för att undvika behovet av att utnyttja en kapacitetsökning finns i följande artiklar i vår utvecklardokumentation:
   * [Bildstorlek](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [Cachelagring av hela sidor](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-verktyg](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
