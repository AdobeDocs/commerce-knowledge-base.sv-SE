---
title: Frågor och svar om den uppdaterade livscykelpolicyn för Adobe Commerce-releaser
description: "Adobe Commerce tillhandahåller kvalitetskorrigeringar för en mindre release i minst 12 månader från det allmänna tillgänglighetsdatumet för nästa mindre programvarurelease. Det sätt på vilket vi tillhandahåller kvalitetskorrigeringar under denna period ändras:"
exl-id: 4aa601d0-ee1d-4f1f-a684-188772a58dd1
feature: Compliance, Support
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 0%

---

# Frågor och svar om den uppdaterade livscykelpolicyn för Adobe Commerce-releaser

## Vad förändras?

Adobe Commerce tillhandahåller kvalitetskorrigeringar för en mindre release i minst 12 månader från det allmänna tillgänglighetsdatumet för nästa mindre programversion. Det sätt på vilket vi tillhandahåller kvalitetskorrigeringar under den här perioden ändras:

* **Tidigare princip:** För närvarande levereras kvalitetskorrigeringarna till föregående rad i EOS-fönstret för 12 månader via vår kvartalsvisa patch-release, vilket gör kvartalsvisa korrigeringar till en kombination av säkerhet och kvalitet.
* **Ny princip:** Från och med 2.4 som den senaste mindre versionsraden kommer versionsfixar för den föregående raden som stöds (2.3) att flyttas till enbart säkerhet. Vi kommer fortfarande att leverera kvalitetskorrigeringar för den föregående raden som stöds under 12-månadersperioden efter att en delversion (som 2.4) och efterföljande delversionsrader släppts, men dessa kommer att göras tillgängliga via [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) och fokusera bara på viktiga frågor.

## När börjar denna policy gälla?

Adobe Commerce 2.3.6 kommer att släppas den 15 oktober 2020 och kommer att vara den sista programfixen för Adobe Commerce 2.3 som kommer att innehålla både kvalitet och säkerhet. Efter 2.3.6 kommer 2.3.x-linjen att bli säkerhetsskyddad och kritiska kvalitetsproblem för 2.3 kan åtgärdas via QPT.

>[!NOTE]
>
>Den enda gången vi släpper en fullversion av 2.3 är om vi behöver uppfylla våra krav på teknik, som PHP eller Elasticsearch. Detta sker under andra kvartalet 2021 med en obligatorisk uppdatering av PHP 7.4, vi kommer att öka gränsen till 2.3.7. Mer information finns i [Stöd för PHP 7.4 i Adobe Commerce 2.3.x](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog-inlägg.

## Vad är en säkerhetsversion?

Endast säkerhetsreleaser innehåller säkerhetskorrigeringar och ingen kvalitet har åtgärdats. Observera dock att våra säkerhetsuppdateringar kan innehålla specifika snabbkorrigeringar när vi anser att dessa är absolut nödvändiga för att köra Adobe Commerce.

## Kommer det fortfarande att finnas en säkerhetsuppdatering för den senaste raden (från och med publiceringen, 2.4)?

Adobe kommer även i fortsättningen att ha säkerhetsversioner för den senaste releaseraden. Processen för dessa beskrivs i [Vi presenterar den nya patchversionen med endast säkerhet](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287) DevBlog-inlägg.

## Vad är Quality Patches Tool?

Läs mer i [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) artikel i vår kunskapsbas för support.

## Vem bör överväga att använda den här nya policyn?

Den nya strategin är avsedd att skapa vägar för handlare att planera strategiskt för de årliga utvecklingskostnaderna för Adobe Commerce, samtidigt som de kan upprätthålla säkerhet och kritisk kvalitet under dessa strategiska cykler. Den kan även användas av handlare som bryr sig om säkerheten över allt annat och som i allmänhet är nöjda med stabiliteten hos äldre stödlinje. Det kan vara enklare att planera och budgetera för dessa uppgraderingar eftersom de blir mer förutsägbara.

## Ska Merchants fortfarande uppgradera till den senaste raden?

I slutändan bör alla affärsmän fortfarande prioritera planeringen för att i tid ta till sig den senaste Adobe Commerce-linjen. Den nya säkerhetslinjen Only och QPT-verktyget är inte avsedda att komplettera den strategiska uppgraderingsplanen för handlare, utan erbjuder snarare flexibilitet för handlare vid planering av deras uppgraderingsplan och möjlighet att snabbt reagera på säkerhets- och kvalitetsfrågor utan att behöva implementera en hel uppgradering.

## Hur får jag kvalitetskorrigeringar för mindre versioner som stöds och som inte är den senaste raden?

Korrigeringar kommer att göras tillgängliga via [Verktyget Kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).

## Hur får jag tag i kvalitetsfixar på den senaste raden?

Den aktuella raden kommer att ha kvalitet som en del av den kvartalsvisa uppdateringen. Om du kontaktar supporten för en korrigering på den senaste raden mellan versionerna kommer de att skicka den via QPT. När du sedan uppgraderar till den version som innehåller den korrigeringen kommer den att användas via kvartalsvis korrigering.

## Vilken typ av kvalitetsproblem kommer att korrigeras för mindre versioner som stöds och som inte är den senaste raden?

Endast viktiga kvalitetsproblem som bryter mot kärnflödena kommer att åtgärdas i föregående rad (2.3) och levereras via QPT.

## Kommer några kvalitetskorrigeringar att ingå i den kvartalsvisa utgåvan för mindre versioner som stöds och som inte är den senaste raden?

Ja, som en del av säkerhetslinjen släpper vi det som Adobe kallar &quot;snabbkorrigeringar&quot; på den raden, som är mycket viktiga problem som påverkar Adobe Commerce-programmet.

## Kommer säkerhetsförbättringar och QPT att levereras samtidigt?

Raden för enbart säkerhet följer kvartalsplanen för lansering och släpps med nomenklaturen -p1. Exempel 2.3.6-p1. Kvaliteten kommer att frisläppas när kvalitetsproblem upptäcks och åtgärdas, och de kommer att göras tillgängliga via QPT.

## Vad gör jag om jag har ett kvalitetsproblem som inte löses i de delversioner som stöds och som inte är den senaste raden eller QPT?

Föregående rad som enbart avser säkerhet innebär att den största fördelen är att den förblir säker. Endast korrigeringsfiler för större problem som bryter kärnflöden kommer att göras tillgängliga via QPT.

Problem som inte påverkar kärnflöden eller som har tillfälliga lösningar kommer att åtgärdas endast på den senaste raden. Adobe uppmuntrar dem som vill ha både kritiska och icke-kritiska korrigeringar att gå över till den senaste linjen.

## Kommer uppgraderingar att bli dyrare eller svårare för Merchants om de inte längre har säkerhetsfunktionerna till dess att säkerhetssupporten upphör?

Teoretiskt sett bör de vara lika höga i kostnader för Merchant i fråga om utvecklingstid så länge de inte har använt ett stort antal kvalitetspatchar. Om en Merchant upptäcker att de behöver eller vill ha mer än en handfull patchar via QPT-verktyget rekommenderar vi att man prioriterar en uppgradering till den senaste versionen av Adobe Commerce. Om man använder ett stort antal kvalitetsuppdateringar i stället för att uppgradera till den aktuella versionen av Adobe Commerce kan utvecklingskostnaderna och uppgraderingskomplexiteten öka när supporten upphör.

## Varför ska jag begränsa mängden högklassiga patchar som levereras via QPT?

Genom att tillämpa många enskilda kvalitetskorrigeringar blir Adobe Commerce-koden mer komplex. Den tillagda komplexiteten kan leda till oförutsägbara ändringar när du uppgraderar till den senaste releasedatan. Därför rekommenderar vi att du använder QPT sparsamt och bara för de mest kritiska korrigeringarna.

## Hur är det med efterlevnad för teknikstackar?

Under en lanseringslinjs livstid kommer det att finnas uppdateringar till olika tekniska stackar som PHP eller Elasticsearch som måste uppgraderas för att följa gällande regler. Vi kommer att meddela våra handlare så mycket som möjligt att de kommer.

Obs! Under andra kvartalet 2021 måste vi uppdatera PHP och Redis på 2.3.x-raden för att hålla oss uppdaterade. Detta gör att raden ökas till 2.3.7. Mer information finns i [Stöd för PHP 7.4 i Adobe Commerce 2.3.x](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog-inlägg.
