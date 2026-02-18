---
title: Allmän felsökningshjälp för anpassad modul
description: I den här artikeln beskrivs allmänna verktyg för att felsöka anpassade moduler i Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Allmän felsökningshjälp för anpassad modul

I den här artikeln beskrivs allmänna verktyg för att felsöka anpassade moduler i Adobe Commerce.

## Problem

Om du upptäcker ett problem med funktionerna i din anpassade modul och du inte får några tydliga felmeddelanden som anger problemet, bör du läsa instansens loggar.

## Lösning

Kontrollera loggarna för att se om det finns poster med namnet på den anpassade modulen i felet.  Beroende på vilka fel som har uppstått kan det bero på att lösningen finns på sig själv eller på att du måste inkludera din användbara Adobe Commerce-logginformation om du vill öppna en [supportanmälan](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket). I följande stycken finns information om loggarnas plats och möjliga lösningar.

### Adobe Commerce (alla distributionsmetoder), Magento Open Source, alla 2.X-versioner

1. Loggplatsen finns på [Adobe Commerce i loggarna för Pro-planarkitekturen för molninfrastruktur](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) i vår kunskapsbas för support.
1. Beroende på vilka fel du hittar, om du vill aktivera, inaktivera eller avinstallera en anpassad modul, innehåller de här artiklarna information om dessa åtgärder:
   * [Aktivera eller inaktivera moduler](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/manage-modules) i utvecklardokumentationen.
   * [Avinstallera moduler](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules) i utvecklardokumentationen.

### Adobe Commerce om molninfrastruktur, alla versioner

1. Loggar platser: [Adobe Commerce i molninfrastrukturloggar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) i utvecklardokumentationen.
1. Beroende på vilka fel du hittar, om du vill aktivera, inaktivera eller avinstallera en anpassad modul, innehåller dessa artiklar i vår dokumentation för utvecklare dessa åtgärder:
   * [Installera, hantera och uppgradera tillägg](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions).
   * [Komponentdistributionsfel](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment).

## Relaterad läsning

I vår utvecklardokumentation:

* [Modulöversikt](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [Fel vid installation av valfria exempeldata](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/errors-installing-optional-sample-data)
* [Undantagshantering](https://developer.adobe.com/commerce/webapi/graphql/develop/exceptions/)
* [Undantag under installationen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/exceptions-during-installation)
* [Kör modulhanteraren](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites)
* [Modulkonfigurationsfiler](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/module-files)
* [Slut på minne](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)
