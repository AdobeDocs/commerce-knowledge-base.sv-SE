---
title: 'Brandvägg för webbaserade program (WAF) med stöd för Fast: Frågor och svar'
description: Brandväggar för webbaserade program (WAF) förhindrar att skadlig trafik kommer in på webbplatser och nätverk genom att filtrera trafik mot en uppsättning säkerhetsregler. Trafik som utlöser någon av reglerna blockeras innan den kan skada dina platser eller nätverk.
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: f384ff9d5d8a8c5c5da20b582c02a2d783b32d7e
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 0%

---

# Brandvägg för webbaserade program (WAF) med stöd för Fast: Frågor och svar

## Hur fungerar Adobe Commerce hanterade molnbaserade WAF (med Fastly-teknik)?

Brandväggar för webbaserade program (WAF) förhindrar att [skadlig trafik](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) kommer in på webbplatser och nätverk genom att filtrera trafik mot en uppsättning säkerhetsregler. Trafik som utlöser någon av reglerna blockeras innan den kan skada dina platser eller nätverk.

Adobe Commerce cloud WAF har en WAF-policy med en regeluppsättning som är utformad för att skydda dina Adobe Commerce webbprogram från en mängd olika attacker.

WAF undersöker webb- och administratörstrafik för att identifiera misstänkta aktiviteter. Den utvärderar GET- och POST-trafik (HTTP API-anrop) och använder regeluppsättningen för att avgöra vilken trafik som ska blockeras. WAF kan blockera en mängd olika attacker, bland annat SQL-injektionsattacker, serveröverskridande skriptattacker (cross-site scripting), dataexfiltreringsattacker och HTTP-protokollöverträdelser.

WAF är en molnbaserad tjänst som inte kräver någon maskin- eller programvara för att kunna installera eller underhålla. Snabb, en befintlig teknikpartner, tillhandahåller programvara och expertis. Deras högpresterande, alltid installerade WAF finns i varje cache-nod över Fastlys globala leveransnätverk.

## Är WAF tillgängligt för alla molnkunder?

Ja, molntjänsten WAF ingår i din Adobe Commerce-prenumeration på molninfrastruktur för både Adobe Commerce på arkitekturen i molninfrastrukturen Starter-planen och Adobe Commerce på arkitekturplanerna i molninfrastrukturen Pro-planen utan extra kostnad. WAF-tjänsten är tillgänglig i produktions- och mellanlagringsmiljöer.

## Uppfyller WAF kraven för PCI DSS 6.6?

Ja.

## Om mitt Adobe Commerce-konto för molninfrastruktur hanterar webbplatser på flera domäner, justeras WAF-profilen för varje domän, eller tillsammans för alla domäner?

WAF ställs in gemensamt för alla domäner med ett enda molnkonto.

## Vilka regler används för WAF?

Regeln i den WAF-profil som tillämpas på din Adobe Commerce i molninfrastruktursproduktionsmiljön baseras på regeluppsättningen OWASP Top 10 Threat Protection, som omfattar vanliga utnyttjanden av webbtjänster. Det innehåller också Adobe Commerce-specifika regler som utvecklats av TrustWave SpiderLabs. Fast&#39;s Security Research Team har också lagt till regler som skyddar din webbplats och ditt nätverk från vanliga attacker: felaktiga IP-adresser, dåliga användaragenter och kända botnet-kommandon och kontrollnoder. Vi aktiverar regler på OWASP Paranoia Level 3 eller lägre, som ger hög säkerhet.

## Hur kommer jag åt loggar?

Om du vill att loggarna ska skickas till loggningsverktyget, bör du samarbeta med din tekniska kontohanterare (TAM) för att snabbt lägga till en loggningsslutpunkt.

## Hur ser en blockbegäran ut?

En blockerad begäran returnerar en 403-sida med en begärandeidentifierare.

Du kan anpassa den här sidan så länge som anpassningen innehåller begärandeidentifieraren. Kontakta din kontoansvarige för mer information.

## Hur uppdaterar vi WAF regeluppsättningar? Hur snabbt kan en WAF-regel ändras eller uppdateras och tillämpas globalt i produktionen?

Som en del av molntjänsten WAF hanterar Fastly regeluppdateringar från kommersiella tredje parter, snabbforskning och öppna källor. De uppdaterar publicerade regler till en policy efter behov eller när ändringar av reglerna är tillgängliga från deras respektive källor. Nya regler som matchar de publicerade regelklasserna infogas också i WAF-instansen för alla tjänster när de har aktiverats. Detta bidrar till att säkerställa omedelbar täckning för nya eller föränderliga explosioner. Du kan granska information [om regeluppdateringar och underhåll](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance) på webbplatsen för snabbdokumentation.

## På vilket sätt skiljer sig Adobe Commerce cloud WAF från WAF lösning Snabbt erbjuder sina direktkunder?

WAF-lösningen som säljs direkt av Fastly är ett prisvärt erbjudande som innehåller bredare regeluppsättningar och ytterligare funktioner som regelanpassning och skydd mot skadlig kod. Adobe Commerce molnlösning för WAF innehåller en deluppsättning av regler för Adobe Commerce och innehåller endast en regeluppsättning för varje kunds produktionsmiljö.

## Vilka typer av säkerhetshot skyddar WAF mot?

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">hot</th>
<th style="width: 497.5px; text-align: left;">WAF-skydd</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">SQL-injektionsangrepp</td>
<td style="width: 497.5px;">Både OWASP ModSecurity Core Rule Set och TrustWave-affärsregeluppsättningen innehåller specifika filter för SQL-injektionsangrepp och dess varianter.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>Injektion på olika ställen</p>
</td>
<td style="width: 497.5px;">OWASP regeluppsättning skyddar mot attacker med injektioner över flera platser. Utnyttja snabbt en bedömningsmekanism för varje begäran som söker efter injektioner på olika platser och andra hot mot ursprunget. Vi poängsätter varje begäran mot hela kärnregeluppsättningen och validerar att poängen för begäran ligger under ett konfigurerbart tröskelvärde för att den ska kunna godkännas.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Anfall med brutal kraft</td>
<td style="width: 497.5px;">Omfattas av OWASP regeluppsättning. Blockerar snabbt även den akuta kraftaktiviteten genom att använda VCL-kod som känner igen specifika källor, förfrågningar eller försök att utnyttja kraften eller överväldigande säkerhetskontroller innan någon trafik når det ursprungliga datacentret.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Nätverksattacker</td>
<td style="width: 497.5px;">Nätverksattacker, eller attacker mot nätverksinfrastruktur, hanteras automatiskt av Fastly. DNS skickas inte automatiskt till ursprungsläget, och trafik som inte matchar en smal HTTP-, HTTPS- eller DNS-profil ignoreras i nätverkets kant. Angripanden mot kontrollprotokoll försvaras genom autentisering av slutpunkter i hela nätverket. Dessutom är de nätverksprotokoll som används inom snabbnätverket hårdgjorda för att säkerställa att de inte kan användas som ett medel för förstärkning eller reflektion. Kunderna ansvarar för att skydda sig mot attacker som går förbi snabbnätverket genom att utnyttja IP-adressutrymmet Fastly Cache, som publiceras till våra kunder som en del av vår CDN-tjänst. Vi rekommenderar att ursprungligt IP-adressutrymme inte publiceras i offentlig DNS för att säkerställa att åsidosättningsattacker inte kan använda dessa adresser som mål.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">JavaScript injektionsangrepp</td>
<td style="width: 497.5px;">WAF regler skyddar mot att skadlig JavaScript-kod infogas i klientkommunikationen med webbtjänster. Vanliga utnyttjandemönster eller bakgrundsmusik filtreras genom WAF för att säkerställa ursprungstjänstens integritet.</td>
</tr>
</tbody>
</table>

## Erbjuds ytterligare funktioner?

Adobe Commerce WAF erbjuder skydd mot OWASP Top-10-hot som en del av PCI-kraven, stöd dygnet runt, alla dagar, inklusive triage för falska positiv information samt versionsuppgraderingar. Följande funktioner stöds inte i standarderbjudandet:

* hastighetsbegränsning
* regelanpassningar
* bockreducering
* skydd mot skadliga program

## Hur påverkas min webbplats prestanda av WAF?

Varje begäran som inte cachelagras har en fördröjning på cirka 1,5 millisekunder (ms) till 20 ms.

## Kan kunderna skapa och ändra IP-svarta listor för att blockera trafik?

Ja, kunderna kan aktivera blockering per land och åtkomstkontrollista (ACL) från administratörsgränssnittet för Adobe Commerce i molninfrastrukturen. Använd dessa funktioner om du vill blockera åtkomst för besökare som kommer från specifika länder eller vissa IP-intervall. Om du vill att blockerade besökare ska se en anpassad sida i stället för en felkod, kan du skapa en anpassad felsida genom att överföra HTML på snabbkonfigurationsmenyn. Se [Skapa en anpassad fel-/underhållssida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) i utvecklardokumentationen.

## Var kan jag kontrollera driftstatusen för min WAF-tjänst?

Övergripande tillgänglighet för WAF-tjänster rapporteras på sidan [Snabbstatus](https://status.fastly.com/). Tillgänglighetsrapportering för enskilda kunders WAF tillhandahålls inte.

## Tillhandahåller Adobe Commerce incidenthantering för WAF?

För närvarande erbjuds inte incidenthantering.

## Har Adobe Commerce ett säkerhetscenter?

Även om Adobe Commerce inte har något säkerhetscenter har vi en säkerhetsverksamhetsprocess som gör att vi kan använda rätt resurser för att hantera säkerhetsincidenter i realtid. Vi erbjuder också support dygnet runt, alla dagar, året om.

Du kan även få säkerhetsnyheter och uppdateringar relaterade till Adobe Commerce från [Säkerhetscenter](https://helpx.adobe.com/security.html).

## Vilken support finns?

WAF Support erbjuder följande resurser för att hjälpa dig att minska tjänsternas konsekvenser av oönskade eller skadliga förfrågningar:

* Onboarding: aktivera, inledande konfiguration och begränsad övervakning av snabbtjänsten/tjänsterna som stöder Adobe Commerce hanterade molnet WAF
* Pågående falskt positiv tripp för att åtgärda fall där WAF blockerar legitim trafik
* Konfiguration av nya standardregler som införs som en del av uppgraderingar av WAF-versioner

Se villkoren för [Cloud SLA](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf) för ytterligare supportinformation, inklusive allvarlighetsdefinitioner, svarstider, kanaler och tillgänglighet.

## Hur kan jag få hjälp om WAF blockerar legitim trafik eller orsakar andra problem?

[Skicka in en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) på [Adobe Commerce Help Center](https://support.magento.com). Ange att biljetten är relaterad till WAF-tjänsten och inkludera ID:t för spärrad begäran.

Adobe Commerce supportsystem spårar kommunikationen mellan våra supporttekniker och en kunds personal. Det här systemet innehåller en tidstämplad kopia av kommunikationen och skickar e-post till kunder och Adobe Commerce personal när biljetterna uppdateras.

Incidentkvittot för alla ärenden som skickas online bekräftas via Adobe Commerce kundhjälpcenter. När ett inlämnat ärende har mottagits ska supporttjänsterna prioriteras i enlighet med de prioriteringsnivåer som anges ovan.

I följande tabell sammanfattas supportkanalerna och tillgängligheten för WAF Support:

<table class="table-basic">
<tbody>
<tr>
<th>Support</th>
<th>Information</th>
</tr>
<tr>
<td>Självbetjäningshjälp online</td>
<td>Obegränsad åtkomst</td>
</tr>
<tr>
<td>Tillgång till incidentrapporter</td>
<td>24/7</td>
</tr>
<tr>
<td>Webbportal</td>
<td>Tillgängligt via Zendesk</td>
</tr>
<tr>
<td>Eskalering av nödsituationer*</td>
<td>Läs artikeln <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html">Adobe Commerce P1 notification hotline</a> för amerikanska och internationella nummer.</td>
</tr>
</tbody>
</table>

*\* Adobe Commerce avgiftsfria telefonlinje för support är endast reserverad för incidenter med prioritet 1. Anrop som inte är prioriterade 1 saktar ned det övergripande svaret på problem*

## Hur luras falska positiva?

Vi har en falskt positiv triageprocess (tillgänglig dygnet runt) för att snabbt ta itu med och lösa situationer där legitima förfrågningar har utlöst en WAF-regel. Falska positiva händelser behandlas som problem med prioritet 1. Som standard kan vårt supportteam uppdatera WAF-policyn omedelbart för att inaktivera regeln som utlöste blockeringshändelsen och tillåta att den berättigade begäran skickas via WAF.

## Vad händer om trafiken till admindelen av Adobe Commerce på molninfrastrukturens webbplats utlöser WAF regler? Kan Adobe Commerce Support lösa problem med blockerad administratörstrafik?

Ja, blockerad administratörstrafik behandlas som ett problem med prioritet 1.
