---
title: Allmän felsökningshjälp för anpassad modul
description: I den här artikeln beskrivs allmänna verktyg för att felsöka anpassade moduler i Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Allmän felsökningshjälp för anpassad modul

I den här artikeln beskrivs allmänna verktyg för att felsöka anpassade moduler i Adobe Commerce.

## Problem

Om du upptäcker ett problem med funktionerna i din anpassade modul och du inte får några tydliga felmeddelanden som anger problemet, bör du läsa instansens loggar.

## Lösning

Kontrollera loggarna för att se om det finns poster med namnet på den anpassade modulen i felet.  Beroende på vilka fel som har uppstått kan det bero på att lösningen finns på sig själv eller på att du måste inkludera din användbara Adobe Commerce-logginformation om du vill öppna en [supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). I följande stycken finns information om loggarnas plats och möjliga lösningar.

### Adobe Commerce (alla distributionsmetoder), Magento Open Source, alla 2.X-versioner

1. Loggplatser:
   * [Adobe Commerce på molninfrastruktur Starter-planens arkitektur loggar](/help/how-to/general/log-locations-directories-for-starter-plan.md) i vår kunskapsbas för support.
   * [Adobe Commerce på Cloud Infrastructure Pro, loggar för planarkitektur](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) i vår kunskapsbas för support.
1. Beroende på vilka fel du hittar, om du vill aktivera, inaktivera eller avinstallera en anpassad modul, innehåller de här artiklarna information om dessa åtgärder:
   * [Aktivera eller inaktivera moduler](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-enable.html) i utvecklardokumentationen.
   * [Avinstallera moduler](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall-mods.html) i utvecklardokumentationen.

### Adobe Commerce om molninfrastruktur, alla versioner

1. Loggar platser: [Adobe Commerce i molninfrastrukturloggar](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) i utvecklardokumentationen.
1. Beroende på vilka fel du hittar, om du vill aktivera, inaktivera eller avinstallera en anpassad modul, innehåller dessa artiklar i vår dokumentation för utvecklare dessa åtgärder:
   * [Installera, hantera och uppgradera tillägg](https://devdocs.magento.com/guides/v2.3/cloud/howtos/install-components.html).
   * [Komponentdistributionsfel](https://devdocs.magento.com/guides/v2.3/cloud/trouble/trouble_comp-deploy-fail.html).

## Relaterad läsning

I vår utvecklardokumentation:

* [Modulöversikt](https://devdocs.magento.com/guides/v2.3/architecture/archi_perspectives/components/modules/mod_intro.html)
* [Fel vid installation av valfria exempeldata](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_sample-data.html)
* [Undantagshantering](https://devdocs.magento.com/guides/v2.3/graphql/develop/exceptions.html)
* [Undantag under installationen](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_exceptions.html)
* [Kör modulhanteraren](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-checklist.html)
* [Modulkonfigurationsfiler](https://devdocs.magento.com/guides/v2.3/config-guide/config/config-files.html)
* [Slut på minne](https://devdocs.magento.com/guides/v2.3/comp-mgr/trouble/cman/out-of-memory.html)
