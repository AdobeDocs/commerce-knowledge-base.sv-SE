---
title: "MDVA-24201: Katalogprisreglerna fungerar inte"
description: MDVA-24201-korrigeringen åtgärdar ett problem där regler för aktivt katalogpris i databasen inte gäller i förgrunden.
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201: Katalogens prisregler fungerar inte

MDVA-24201-korrigeringen åtgärdar ett problem där regler för aktivt katalogpris i databasen inte gäller i förgrunden.

Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.3.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.3.3

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce i molninfrastruktur och Adobe Commerce lokalt 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättning</u>:

Installera en ny Magento-instans med exempeldata.

<u>Steg som ska återskapas</u>:

1. Logga in på **Admin panel** > **Marknadsföring** > **Katalogprisregel** > **Lägg till ny regel** och gör följande inställningar:
   1. Ange **regelnamn**.
   1. Ange **Aktiv** = *Nej.*
   1. Ange villkor: **Kategori** = *4*. (Exempel: väskor)
   1. Ange åtgärder:
      1. Ange **Använd som**   **procent av originalet**.
      1. Ange **Rabattbelopp** = *10*.
      1. Spara och fortsätt sedan redigera.
   1. Klicka på **Schemalägg ny uppdatering**:
      * Ange **regelnamn**.
      * Ange **Aktiv** = *Ja*.
      * Spara.
1. Gå till serverdelen och kör:

   `php    bin/magento cron:run`

<u>Förväntade resultat</u>:

Priserna på produkterna i kategori 4&quot;Bags&quot; bör sänkas med 10 % av det ursprungliga priset, enligt regeln om katalogpris, som förväntat.

<u>Faktiska resultat</u>:

Inga prisändringar inträffar trots att katalogprisregeln är aktiv.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
