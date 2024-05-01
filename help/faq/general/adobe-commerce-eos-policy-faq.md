---
title: Vanliga frågor om Adobe Commerce-programvarans slut
description: Följande frågor och svar är avsedda att hjälpa handlare, utvecklare och partners att förstå konsekvenserna av Adobe Commerce publicerade End of Support-datum (EOS) för berörda versioner av Adobe Commerce.
exl-id: ec147307-46eb-4a3a-8572-a014b091c58a
feature: Best Practices, Compliance, Console
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '1733'
ht-degree: 0%

---

# Vanliga frågor om Adobe Commerce-programvarans slut

Följande frågor och svar är avsedda att hjälpa handlare, utvecklare och partners att förstå konsekvenserna av Adobe Commerce publicerade End of Support-datum (EOS) för berörda versioner av Adobe Commerce.

## Allmänna bestämmelser

### Var hittar jag supportdatum för alla versioner av Adobe Commerce?

Du hittar Adobe Commerce livscykelpolicy och datum för programsupport i [Adobe Commerce Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf). Vi publicerar också slutdatum (EOS) på vår [dokumentationssida för utvecklare](https://devdocs.magento.com/release/released-versions.html).

### Vad innebär det när Adobe slutar stödja en version av Adobe Commerce?

När Adobe upphör med stödet för en version av Adobe Commerce kan du förvänta dig följande:

* Adobe Commerce kommer inte längre att skapa ytterligare produktändringar för den versionen (inklusive ändringar av funktionalitet, kvalitet, säkerhet och PCI-kompatibilitet).
* Hämtningsbegäranden från communityn kommer inte längre att accepteras eller sammanfogas för EOS-versionen. Tillägg i Commerce Marketplace som bara är kompatibla med versioner av Adobe Commerce som inte stöds tas bort.
* Onlinedokumentation för de versioner som inte stöds tas bort (t.ex. dokumentation för utvecklare).
* Supportärenden som skickas in efter att en Adobe Commerce-version har upphört med supporten kommer inte att lösas (mer teknisk supportinformation finns nedan).

### Vilka följder får handlare som använder Adobe Commerce som inte stöds?

Vi rekommenderar starkt att du bara använder programvara som stöds.

Om du bestämmer dig för att fortsätta använda programvara som har fått support kommer du inte längre att få viktiga produktuppdateringar eller teknisk support, som ofta innehåller de senaste säkerhetsuppdateringarna. Om du använder program som inte stöds kan det påverka följande områden:

**Säkra shoppingupplevelser:**

* Ni måste spendera resurser på att utvärdera och anlita tredjepartsleverantörer för att kunna erbjuda säkerhetssupport, korrigeringar och uppdateringar.
* När en version av Adobe Commerce inte längre stöds är den versionen inte längre [PCI-kompatibel](https://www.pcisecuritystandards.org/pci_security/maintaining_payment_security). När detta inträffar kan du bli föremål för böter, indragna kreditkortsmöjligheter eller andra påföljder.
* Eftersom de flesta installationer tenderar att vara inriktade på installationer som inte är uppdaterade med de senaste säkerhetsuppdateringarna rekommenderar vi alltid att handlarna håller sin programvara uppdaterad och installerar säkerhetsuppdateringar så snart de blir tillgängliga. Det är upp till handlaren att skydda sin onlinebutik med lämpliga skyddsåtgärder och säkerhetskontroller för att skydda sin webbplats och sina kunders personuppgifter. Ett av de bästa sätten att göra detta är att ha de senaste korrigeringarna, programuppdateringarna och programuppdateringarna installerade samt att kontinuerligt övervaka platsen och Admin Console för ovanlig aktivitet.

**Effektivt och effektivt**

* Eftersom Adobe Commerce programversioner inte stöds finns det en minskande grupp av utvecklare och partners som kan ge support för gamla versioner när de orienterar sin verksamhet efter nyare tekniker. I allmänhet innebär det att mängden och kvaliteten på talangen för programvaruunderhåll minskar, samtidigt som kostnaden för att underhålla programvaran ökar.
* För Adobe Commerce-program som inte stöds kan kringutrustning och beroenden också nå sin egen livscykel (t.ex. PHP, MYSQL, REDIS, SOLR). Detta gör det allt svårare att hantera och underhålla en säker och kompatibel webbplats.
* Extension-utvecklare fokuserar också allt mer på den senaste tekniken och kompatibla plattformar. Det innebär att de kanske inte kan fortsätta att underhålla tillägg för versioner av Adobe Commerce som inte stöds.
* Användning av versioner av Adobe Commerce som inte stöds leder ofta till att man spenderar mer pengar och resurser på att underhålla en gammal plattform istället för att använda dessa resurser för att fortsätta med innovationer och tillväxt.

**Grovt aggressiv**

* Adobe fortsätter att investera i nya tekniker och funktioner. Genom att hålla programvaran uppdaterad kan ni dra nytta av nyare tekniker och funktioner som kan hjälpa ert företag att arbeta mer strategiskt och växa ännu snabbare.

### Vilka är några exempel på hur handlare kan dra nytta av ny teknik genom att hålla sig à jour med sina Adobe Commerce-program?

Det finns flera sätt att hålla dig à jour med dina Adobe Commerce-program:

* Utöver att hålla plattformen uppdaterad med de senaste säkerhetsskyddseffekterna, inklusive PCI-kompatibilitet, kan en uppgradering till en version som stöds ge bättre prestanda och skalbarhet och ge dig tillgång till de senaste innovationerna.
* Adobe Commerce 2.4.4, som kommer den 12 april 2022, är ett nytt steg framåt när det gäller affärsfunktioner, prestanda och skydd. Det utgör grunden för de kommande åren av innovation i Adobe som hjälper till att stärka affärsverksamhetens återhämtningsförmåga. Den senaste versionen av PHP 8.1 gör det möjligt för handlare att framtidssäkra sin digitala e-handelsverksamhet med:
   * Snabbare åtkomst till innovativa funktioner som SaaS-tjänster, som Recommendations, Betala-tjänster och Live Search
   * Enklare och mer kostnadseffektivt underhåll och uppgraderingar
   * Fortsatt flexibilitet för att anpassa och uppfylla unika affärsbehov
   * Betydande prestandaökningar och skalbarhet
   * Bättre utvecklarupplevelser och verktyg för att övervaka plattformens hälsa

### Vad bör jag göra för att undvika att supportärenden upphör?

Er handelsplattform är ett viktigt affärssystem för ert företag och att hålla er uppdaterade och aktuella är en viktig pågående investering i företaget. De senaste teknologierna och säkerhetsuppdateringarna för er digitala butik är viktiga på många nivåer och kan bidra till att förbättra innovationer och tillväxt.

Att gå över till den senaste versionen av Adobe Commerce kan ta tid och resurser att bli bra. Det är bäst att ni planerar så långt före supportdagens slut som möjligt för att försäkra er om att ni har den tid och de resurser som behövs för att uppnå era strategiska mål i tid och inom budgeten. Adobe har publicerat [2.4 Upgrade Guide](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) som innehåller bästa praxis och tekniska steg att följa, samt verktyg och resurser som du kan använda när du uppgraderar.

En annan viktig faktor är att förbehålla utvecklare och partners resurser så tidigt som möjligt. Partnertid och resurser bokas ofta långt före supportdatumet, vilket resulterar i betydligt färre resurser för att hjälpa till med migreringsprojekt. Vi rekommenderar att du har en treårig löpande plan som du diskuterar årligen med minimum och ser till att nästa år planeras och budgeteras för. Använd [Adobe&#39;s release calendar](https://devdocs.magento.com/release/) för att hålla reda på releasedatum.

### Kan jag använda en tredjeparts tjänsteleverantör för programsupport när Adobe Commerce Support upphör?

Ja, du kan leta efter säkerhetsföretag, utvecklare eller partners som kan ge support för versioner av Adobe Commerce som inte stöds. Det är ditt ansvar att utvärdera dessa leverantörer, certifiera dem på nytt om det behövs samt identifiera och lösa pågående säkerhetshot som kan påverka ert företag och era kunder.

### Jag har en licens för Adobe Commerce som gäller efter det angivna supportdatumet eller den versionen. Kommer Adobe att fortsätta tillhandahålla programsupport för min version som inte stöds under hela licensperioden om jag väljer att inte gå över till en version som stöds?

Adobe Commerce-licensen ger dig rätt att få tillgång till och använda allmänt tillgängliga versioner av Adobe Commerce, inklusive att få tillgång till och använda versioner som inte stöds. Oavsett om programversionen stöds eller inte måste du fortsätta att hålla dig uppdaterad med de aktuella licensavgifterna för att kunna fortsätta använda Adobe Commerce. Detta upphör när ditt Adobe Commerce-avtal upphör.

En Adobe Commerce-licens ger ingen programsupport för versioner som har nått och passerat sitt sista supportdatum. Viktigt är att om du fortsätter att använda program som inte stöds måste du hantera och betala för dina egna säkerhetsuppdateringar och omcertifiering av PCI-kompatibilitet, och du får troligtvis ytterligare säkerhetsrisker och ansvar.

### &quot;Stänger en programversion&quot; när supportdatumet är inne och passerat?

Nej, Adobe Commerce&quot;stängs inte&quot; när supportdatumet har nåtts eller passerats. Din licens gäller även för Adobe Commerce-program som inte stöds så länge ditt konto är i gott skick, men du ansvarar för omcertifieringen av PCI-kompatibilitet och kan inte längre skicka supportärenden. Viktigast av allt är att du inte längre får säkerhetsuppdateringar som hjälper dig att skydda din digitala butik.

### Kan jag fortsätta att använda Adobe Commerce när licensen har gått ut?

När Adobe Commerce-licensen upphör måste du sluta använda Adobe Commerce och ta bort alla versioner av programmet. Så länge ditt konto är i gott skick ger Adobe Commerce-licensen dig rätt att få tillgång till och använda de allmänt tillgängliga versionerna av Adobe Commerce.

## Tekniska avsättningar

### Kommer supportärenden som har öppnats FÖRE supportdatumet för en programversion att fortsätta att bearbetas till en lösning även efter supporttidens slut?

Ja, supportärenden som öppnats före supportdatumet för en programversion kommer att fortsätta att behandlas och lösas även om supportdatumet för den programversionen har gått ut. Att lösa supportärenden kan dock vara beroende av om upplösningen är beroende av komponenter som ligger utanför Adobe Commerce kontroll (t.ex. PHP, jQuery) som inte längre stöds eller som inte längre stöds. I dessa fall kan supportanmälan lösas genom att du uppmanas att uppgradera till den senaste versionen.

### Om jag öppnar en biljett för en programversion där programvarusupporten upphör snart, prioriterar då Adobe biljetterna så att de löses innan supportdatumet är slut?

Nej, Adobe prioriterar inte om supportärenden baserat på slutdatumet för dessa programversioner. Supportärenden hanteras baserat på interna algoritmer som baseras på biljettens kontaktorsak, miljö och påverkan på verksamheten.

### Finns det en varning som påminner säljarna om att supporten upphör att gälla innan supportdatumet är slut?

Nej, det finns inga påminnelser som meddelar supportanvändare om att supportdatumet kommer att upphöra. Det åligger den som öppnar biljetten att få veta när supportdatumen för den Adobe Commerce-version de är installerade har löpt ut, vilket finns på vår [Adobe Commerce Software Lifecycle Policy](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

### Om en supportanmälan för en programversion öppnas EFTER supportdagens slut för den versionen, kommer den fortfarande att åtgärdas?

Nej, Adobe Commerce kan inte lösa supportärenden som öppnats efter supportdatumet för den programversionen.
