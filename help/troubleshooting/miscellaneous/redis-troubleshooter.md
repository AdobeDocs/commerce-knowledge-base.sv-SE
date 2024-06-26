---
title: Redis-felsökning på Adobe Commerce
description: Den här artikeln är ett felsökningsverktyg för Adobe Commerce lokalt och Adobe Commerce på återförsäljare av molninfrastruktur som har problem med Redis. Klicka på varje fråga för att visa svaret i varje steg i felsökaren. Beroende på dina symtom och din konfiguration visar felsökaren hur du felsöker version- och minnesproblem och optimerar prestanda.
exl-id: 241abcfd-33b8-449b-b385-32950bd26320
feature: Services, Support
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Redis-felsökning på Adobe Commerce

Den här artikeln är ett felsökningsverktyg för Adobe Commerce lokalt och Adobe Commerce på återförsäljare av molninfrastruktur som har problem med Redis. Klicka på varje fråga för att visa svaret i varje steg i felsökaren. Beroende på dina symtom kommer felsökaren att förklara hur du kan felsöka version- och minnesproblem och optimera prestanda.

## Steg 1 - Redis-problem {#step-1}

+++Redis issue?

a. JA - Fortsätt till [Steg 2](#step2)</a>.

b. NEJ - Återgå till [support.magento.com](https://support.magento.com/hc/en-us) och söka efter relevanta felsökningsartiklar.

+++

## Steg 2 - Bekräfta installerade Redis-korrigeringar {#step-2}

+++Aktuella Redis-korrigeringar installerade?

a. JA - Fortsätt till [Steg 3](#step3)</a>.

b. NEJ - Kontrollera att du har den senaste versionen av paketet `magento-cloud-patches` installerade. Paketet innehåller de nödvändiga plåstren för Redis. Gå till [GitHub magneto-cloud-patches](https://github.com/magento/magento-cloud-patches/).

+++

## Steg 3 - Bekräfta att Redis-versionen stöds {#step-3}

++ På Redis version 3.2 eller 5.0?

Kontrollera genom att köra följande kommandon i CLI. Pro eller Staging: `$ redis-cli -p %port-number% info | grep redis_version`, där `%port-number%` är numret på den port som finns i `app/etc/env.php` eller genom att köra något av följande kommandon: `$ vendor/bin/ece-tools env:config:show | grep -i redis -A 3` eller `$ cat app/etc/env.php | grep redis -A 3` Start eller integrering: `$ redis-cli -h 'redis.internal' info | grep redis_version`

a. JA - Fortsätt till [Steg 4](#step4).

b. NO - Adobe Commerce stöder Redis version 3.2 och 5.0. Om du kör Adobe Commerce i molninfrastruktur 2.3.3 eller senare rekommenderar vi att du uppgraderar till Redis 5. Om du vill se installationsstegen för Adobe Commerce i molninfrastrukturen Pro-planarkitekturen, integrerings- och startmiljöerna, inklusive huvudgrenen, kan du läsa [Adobe Commerce i molninfrastruktur > Konfigurera Redis-tjänst](https://devdocs.magento.com/cloud/project/services-redis.html)</a> i vår dokumentation för utvecklare. **Du måste [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att ändra tjänstkonfigurationen i Pro-arkitekturens produktions- och mellanlagringsmiljöer. Dessutom rekommenderas en utökad Redis-cacheimplementering för Adobe Commerce i molninfrastrukturen och Adobe Commerce lokalt 2.3.5+. Den här typen av Redis-cacheimplementering innehåller förbättringar som minimerar antalet frågor till Redis som utförs på varje Adobe Commerce-begäran. Om du vill se steg går du till [Utökad Redis-cacheimplementering Adobe Commerce 2.3.5+](https://support.magento.com/hc/en-us/articles/360049292532) i vår kunskapsbas för support. För alla andra Adobe Commerce-användare, se [Adobe Commerce Configuration Guide > Configure Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/config-redis.html) i vår dokumentation för utvecklare, för steg.

+++

## Steg 4 - Verifiera den senaste versionen av ECE-verktygen {#step-4}

+++Har du den senaste versionen av [ECE-verktyg > v2002.1.1](https://github.com/magento/ece-tools/releases)?

Kontrollera vilken version du har genom att köra kommandot i CLI/Terminal: `$php vendor/bin/composer info magento/ece-tools`.

a. JA - Fortsätt till [Steg 5](#step5).

b. NEJ - [Uppgradera ECE-verktyg](https://devdocs.magento.com/cloud/project/ece-tools-update.html) till den senaste versionen.

+++

## Steg 5 - Utvärdera nätverkstrafik {#step-5}

+++Finns det mycket nätverkstrafik mellan appen och Redis?

a. JA - Prova följande: För en icke-delad arkitektur ska du kontrollera att [sekundär anslutning](/help/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.md) används. För en delad arkitektur [L2-cache måste aktiveras](https://devdocs.magento.com/guides/v2.4/config-guide/cache/two-level-cache.html).

b. NO - Konfigurera konfiguration av L2-cache med [Uppdaterar Redis Backend](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend). Fortsätt till [Steg 6](#step6).

+++

## Steg 6 - Kontrollera webbplatshastigheten {#step-6}

+++Fungerar webbplatsen fortfarande långsamt när L2-cachen har aktiverats?

a. JA - Kontrollera den tillfälliga katalogen `/dev/shm` för att se om du behöver öka utrymmet. Om du behöver mer utrymme [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
b. NEJ - Att aktivera L2-cache verkar ha löst dina Redis-problem.

+++

[Tillbaka till steg 1](#step-1)
