---
title: 'MDVA-34591: Beräkningar av kundprisregler fungerar inte som förväntat'
description: Korrigeringen MDVA-34591 åtgärdar ett problem där kundvagnsprisregeln med **maximal mängdrabatt används för** inte fungerar korrekt om flera kundvagnsprisregler tillämpas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Korrigerings-ID är MDVA-34591. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.
exl-id: 1fa196bb-aab1-4364-a1b0-7c31d6d27d6d
feature: Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-34591: Beräkningar av kundprisregler fungerar inte som förväntat

Korrigeringen MDVA-34591 åtgärdar ett fel där kundvagnsprisregeln med **maximal kvantitetsrabatt tillämpas på** inte fungerar korrekt om flera kundvagnsprisregler tillämpas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Korrigerings-ID är MDVA-34591. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.6

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.0-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till Admin och skapa följande två regler:

   * Regel 1: $10 av maximalt tre artiklar i kundvagnen. Ange prioritet = *3*.
   * Regel 2: 50 % rabatt på alla produkter i kundvagnen. Ange prioritet = *1*.

1. Gå till butiken.

1. Lägg åtta kvantiteter i en produktuppsättning till pris = *$51* i kundvagnen.

1. Kontrollera rabattbeloppet i kundvagnen.

<u>Förväntade resultat</u>:

Den korrekta beräknade rabatten är $234 som förväntat.

* Beräkningar:

  Matchande kundvagnsprisregler: regel 2, regel 1\
  Använd regel 2 (50 % rabatt), så rabatt = $204\
  Använd regel 1 (10 av 3 objekt), så rabatt = $30\
  Total rabatt = MIN ( 408/2 + 10x3, 8 &#42; 51) = MIN (204 + 30, 8 &#42; 51) = $234

<u>Faktiska resultat</u>:

Rabatten beräknas felaktigt till 153 USD, vilket beror på fel kvantitet som används för att beräkna maximalt rabattvärde, eftersom det fasta rabattbeloppet tillämpas oavsett produktens belopp i kundvagnen.

* Beräkningar:

  Matchande kundvagnsprisregler: regel 2, regel 1\
  Använd regel 2 (50 % rabatt), så rabatt = $204\
  Använd regel 1 (10 av 3 objekt), så rabatt = $30\
  Total rabatt = MIN (2004 + 30, 3 &#42; 51) = $153

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
