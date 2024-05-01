---
title: Borttagning av åtkomst från Blackfire till Adobe Commerce i molninfrastruktur
description: Den 11 april 2020 kommer kostnadsfri åtkomst till prestandaövervakning i Blackfire inte längre att ingå i Adobe Commerce för Cloud Infrastructure Pro-planarkitekturen eller Adobe Commerce för prenumerationer på molninfrastruktursarkitekturen i Starter-planen.  Du kommer inte längre att kunna logga in på ditt Blackfire-konto. Du kan fortsätta att använda Blackfire efter 11 april genom att köpa en licens direkt via Blackfire.io. Handlare från Adobe Commerce som ännu inte köpt licenser direkt från Blackfire före detta datum kommer att få sina kostnadsfria licenser som tillhandahålls av Adobe inaktiverade Blackfire. Dessutom inaktiveras funktionaliteten för att skapa nya rapporter med profileringsverktyget. Det är fortfarande möjligt för kunder som använder Pro-arkitektur som är värd för molninfrastruktur att få kostnadsfri övervakning av infrastrukturprestanda via New Relic Infrastructure.
exl-id: bf33c2c6-e9b3-474a-a127-909b51dff92f
feature: Cloud, Paas
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Borttagning av åtkomst från Blackfire till Adobe Commerce i molninfrastruktur

Den 11 april 2020 kommer kostnadsfri åtkomst till prestandaövervakning i Blackfire inte längre att ingå i Adobe Commerce för Cloud Infrastructure Pro-planarkitekturen eller Adobe Commerce för prenumerationer på molninfrastruktursarkitekturen i Starter-planen.  Du kommer inte längre att kunna logga in på ditt Blackfire-konto. Du kan fortsätta att använda Blackfire efter 11 april genom att köpa en licens direkt via Blackfire.io. Handlare från Adobe Commerce som ännu inte köpt licenser direkt från Blackfire före detta datum kommer att få sina kostnadsfria licenser som tillhandahålls av Adobe inaktiverade Blackfire. Dessutom inaktiveras funktionaliteten för att skapa nya rapporter med profileringsverktyget. Det är fortfarande möjligt för kunder som använder Pro-arkitektur som är värd för molninfrastruktur att få kostnadsfri övervakning av infrastrukturprestanda via New Relic Infrastructure.

**Om du vill fortsätta använda Blackfire**:

1. Du måste köpa en licens hos Blackfire direkt.
1. Konfigurera sedan Blackfire med dessa [steg](https://blackfire.io/docs/integrations/paas/magentocloud).
1. Om du får problem med installationen kan du [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att begära hjälp. Specifika frågor om Blackfire kan du kontakta Blackfire support direkt på [support@blackfire.io](mailto:support@blackfire.io).

## Om du får fel när du kör en distribution:

Om du får fel relaterade till Blackfire när du kör en distribution gör du följande:

1. Ta bort Blackfire från konfigurationen. Redigera `.magento.app.yaml` och ta bort Blackfire från körningsavsnittet:

   ```YAML
   ...
   # Enable extensions required by Magento 2
   runtime:
     extensions:
     - redis
     - xsl
     - json
     -**blackfire**
      - imap
   ...
   ```

1. Slutför detta i den lokala utvecklingsmiljön och gå vidare till molnet.

Endast [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om följande fel visas när du har kört en distribution:

*PHP-varning: PHP-start: Det gick inte att läsa in det dynamiska biblioteket &quot;Blackfire.so&quot; (försökte: /usr/lib/php/20180731-zts/blackfire.so (/usr/lib/php/20180731-zts/blackfire.so: cannot open shared object file: No such file or directory), /usr/lib/php/20180731-zts/blackfire.so.so (/usr/lib/php/20180731-zts/blackfire.so.so: cannot open shared object file: No such file or directory) i Okänd på rad 0*

Detta fel innebär att plugin-programmet Blackfire måste uppdateras och inte kan läsas in.

**Om du vill använda New Relic Infrastructure**:

Mer information om hur du får åtkomst till New Relic infrastruktur finns i [Använd New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) i vår kunskapsbas för support.
