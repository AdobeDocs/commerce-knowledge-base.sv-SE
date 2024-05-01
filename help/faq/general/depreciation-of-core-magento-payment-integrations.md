---
title: Avskrivning av Adobe Commerce grundläggande betalningsintegreringar
description: På grund av betaltjänstdirektivet PSD2 (se närmare information om [Payment Services Directive](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) i vår användarhandbok) och den fortsatta utvecklingen av många API:er finns det risk för att ett antal av Adobe Commerce kärnbetalningsintegreringar blir inaktuella och inte längre uppfyller säkerhetskraven i framtiden. Därför har många grundläggande betalningsintegreringar tagits bort eller kommer att tas bort, och vi rekommenderar en övergång till motsvarande tillägg för Commerce Marketplace. Läs resten av artikeln nedan om du vill se vilka borttagningar av betalningsintegreringar som gjorts nyligen. Var och en av länkarna **Status** finns i användarhandboken. **Integrationerna nedan kommer att tas bort från Adobe Commerce version 2.4.0 och har tagits bort från version 2.3.**
exl-id: c2c4b3b6-409d-466f-a4f3-dfe13ac7f972
feature: Compliance, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Avskrivning av Adobe Commerce grundläggande betalningsintegreringar

På grund av betaltjänstdirektivet PSD 2 (se närmare information om [Betalningstjänster](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) i vår användarhandbok) och i den fortsatta utvecklingen av många API:er finns det risk för att ett antal Adobe Commerce kärnbetalningsintegreringar blir inaktuella och inte längre uppfyller säkerhetskraven i framtiden. Därför har många grundläggande betalningsintegreringar tagits bort eller kommer att tas bort, och vi rekommenderar en övergång till motsvarande tillägg för Commerce Marketplace. Läs resten av artikeln nedan om du vill se vilka borttagningar av betalningsintegreringar som gjorts nyligen. Varje **Status** finns i användarhandboken. **Integrationerna nedan kommer att tas bort från Adobe Commerce version 2.4.0 och har tagits bort från version 2.3.**

<table style="height: 243px;" width="712">
<tbody>
<tr>
<td style="width: 225.455px;"><strong>Integrering av betalningssätt</strong></td>
<td style="width: 226.364px;"><strong>Status</strong></td>
<td style="width: 226.364px;"><strong>Rekommendation Adobe Commerce 2.X</strong></td>
</tr>
<tr>
<td style="width: 225.455px;">Worldplay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Borttagen sedan 2.3.5</a><br>2.4.0 - kommer att tas bort helt</td>
<td style="width: 226.364px;">Fråga din betalningsleverantör vilken lösning de rekommenderar för att uppfylla PSD2-kraven.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Borttagen sedan 2.3.4</a><br>2.4.0 - kommer att tas bort helt</td>
<td style="width: 226.364px;">Använd <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">officiell förlängning</a> från Commerce Marketplace istället.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net (direktinlägg)</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Borttagen sedan 2.3.1</a><br>2.4.0 - kommer att tas bort helt</td>
<td style="width: 226.364px;">Använd <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">officiell förlängning</a> från Commerce Marketplace istället.</td>
</tr>
<tr>
<td style="width: 225.455px;">CyberSource</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Borttagen sedan 2.3.3</a><br>2.4.0 - kommer att tas bort helt</td>
<td style="width: 226.364px;">Använd <a href="https://marketplace.magento.com/cybersource-global-payment-management.html">officiell förlängning</a> från Commerce Marketplace istället.</td>
</tr>
<tr>
<td style="width: 225.455px;">eWay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Borttagen sedan 2.3.3</a><br>2.4.0 - kommer att tas bort helt</td>
<td style="width: 226.364px;">Fråga din betalningsleverantör vilken lösning de rekommenderar för att uppfylla PSD2-kraven.</td>
</tr>
</tbody>
</table>

**Observera att integreringen av betalningsmetoden PayPal inte kommer att bli inaktuell eller tas bort och att den fortfarande stöds i alla 2.3.x- och 2.4.x-versioner.**

## Så här håller du dina betalningar skyddade och flyttar framåt

För alla distributioner av Adobe Commerce och Magento Open Source som fortfarande använder föråldrade betalningsintegrationer bör du följa rekommendationerna nedan för att säkerställa att dina kunders betalningar är säkra, att betalningarna inte är nekade och för att förbereda uppgraderingen till Adobe Commerce 2.4.0:

* Installera och konfigurera det officiella betalningsmetodtillägget från [Commerce Marketplace](https://marketplace.magento.com/extensions/payments-security/payment-integration.html?_ga=2.108129217.2105547619.1564067043-238341041.1564067043) enligt tabellen ovan.
* Inaktivera inaktuella betalningsintegreringar i Admin (ange **Aktiverad** config option to *Nej* ) så att de inte längre visas som betalningsalternativ i din butik. Se till att alla nya order betalas via tilläggsintegreringen i stället.
* Eftersom den nya integrationen från Commerce Marketplace inte kommer att kunna behandla betalningstransaktioner som gjorts med en inaktuell betalningsintegrering, rekommenderar vi att båda betalningsmetoderna används under en period parallellt, men endast för slutförande av redan bokförda transaktioner och möjliga återbetalningar. Om du vill göra det ska du inaktivera den inaktuella betalningsmetoden, men låta alla konfigurationsfält vara ifyllda.
