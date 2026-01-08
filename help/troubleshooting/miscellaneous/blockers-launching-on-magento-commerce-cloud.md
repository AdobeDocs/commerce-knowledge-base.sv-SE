---
title: Blockerare som startar på Adobe Commerce i molninfrastruktur
description: Den här artikeln innehåller en korrigering för blockering av starter på Adobe Commerce i molninfrastruktur, bland annat problem med Fastly config, SSL-certifikat, 301-omdirigeringar och prestanda för statiska resurser.
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: d653957b94127e8b1d37a66c069a618f34ac5af9
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# Blockerare som startar på Adobe Commerce i molninfrastruktur

Den här artikeln innehåller en korrigering för blockering av starter på Adobe Commerce i molninfrastruktur, bland annat problem med Fastly config, SSL-certifikat, 301-omdirigeringar och prestanda för statiska resurser.

## &#x200B;1. Snabb konfiguration

[Fast](https://www.fastly.com/) är ett CDN-nätverk (Varnish-based Content Delivery Network) som används för att leverera statiska resurser. Det krävs för Adobe Commerce i molninfrastruktur i produktionsmiljöer, så det är viktigt att konfigurera Snabbt och testa webbplatsen (UAT) med Snabbt aktiverad och konfigurerad - både i produktionsmiljöer och i produktionsmiljöer.

>[!WARNING]
>
>När FPC (Full Page Cache) är aktiverat fungerar webbplatsen annorlunda. Kontrollera att du testar den innan du publicerar den.

Processen med snabb konfiguration beskrivs i detalj i avsnittet [Konfigurera fast](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=sv-SE) i användarhandboken. Nedan beskrivs de viktiga stegen.

### 1a. Kontrollera att du har den senaste versionen av snabbmodulen installerad

Kontrollera att du har den senaste versionen av modulen Snabbt installerad för att få de senaste funktionerna och förbättringarna. Om du vill kontrollera om du har den senaste versionen av Snabbt går du igenom [Uppgradera snabbmodulen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=sv-SE#upgrade-the-fastly-module) i användarhandboken. Mer information finns i [Konfigurera snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=sv-SE) i användarhandboken.

### 1b. Aktivera och konfigurera snabbt med Commerce Admin

Mer information finns i [Få dina inloggningsuppgifter snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=sv-SE#get-fastly-credentials) i användarhandboken.

### 1c. Ladda upp VCL-fragment snabbt

Mer information finns i [Överför VCL till Snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=sv-SE) i användarhandboken.

Du kan också [skapa och lägga till egna VCL-fragment](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=sv-SE).

### 1d. Konfigurera DNS för snabb


Mer information finns i den här artikeln: [Konfigurera snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=sv-SE#update-dns-configuration-with-development-settings) i användarhandboken.

## &#x200B;2. Giltigt SSL-certifikat (TLS)

Problem: Utan ett giltigt och fungerande SSL-certifikat kan du inte testa externa betalningsmetoder på sidan Utcheckning i mellanlagringsmiljön.

Rekommendation **:** Begär ditt delade SSL-certifikat för mellanlagrings- eller Live-domännamn.


## &#x200B;3. Konfigurera och testa 301 omdirigeringar

Problem: 301 omdirigeringar har inte tillhandahållits eller är felaktigt konfigurerade, vilket gör att din butik hamnar i SEO-rankningar och söklistor.

Rekommendation **:** Konfigurera och testa de 301 omdirigeringarna noggrant.

Om du migrerar från en gammal webbplats till en ny dirigeras 301 om så att dina kunder kan gå från de tidigare indexerade gamla sidorna till rätt sidor i din nya butik:

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**Relaterade artiklar:**

* [Dirigerar om via route.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html?lang=sv-SE) i användarhandboken.
* [Dirigerar om via molnkonsolen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=sv-SE) i vår användarhandbok.
* [URL-omskrivningar](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html?lang=sv-SE) i användarhandboken.

## &#x200B;4. Resursprestanda

Problem: Statiska resurser hanteras långsamt så att webbplatsen har dålig prestanda (lång inläsningstid, multimediainnehåll som inte visas osv.). Statiska resurser på webbplatsen är CSS-resurser, bilder, videor, bifogade dokument och mycket annat. Det sätt på vilket de är organiserade och betjänade är en viktig faktor för webbplatsens prestanda.

Rekommendation: Om du vill identifiera möjliga orsaker till dålig prestanda bör du använda [Adobe Commerce Performance Toolkit](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) för prestandatestning. Du kan även använda dessa verktyg från tredje part:

* [Beskyddare](https://www.joedog.org/siege): HTTP-belastningstestning och testverktyg; stöder grundläggande autentisering, cookies, HTTP-, HTTPS- och FTP-protokoll.
* [Jmeter](https://jmeter.apache.org/): Ett välrenommerat lasttestnings- och prestandamätningsverktyg. Hjälper till att mäta prestanda för spikad trafik, t.ex. för flashförsäljning.
* [New Relic](https://support.newrelic.com/): Söker efter processer och områden på webbplatsen som orsakar långsamma prestanda med spårad tid per åtgärd, som överföring av data, frågor, Redis osv.
* [WebPageTest](https://www.webpagetest.org/) (kostnadsfritt) och [Passagerare](https://www.pingdom.com/) (betalt): Realtidsanalys av webbplatssidorna läses in med olika ursprungsplatser.

Du kan också överväga [minification](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=sv-SE) för CSS, JavaScript och HTML.

**Relaterade artiklar:**

* [Testa distributionen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html?lang=sv-SE) i utvecklardokumentationen.
