---
title: "MDVA-30862: Felaktigt orderdatum på utskriven PDF-faktura"
description: MDVA-30862-korrigeringen åtgärdar ett problem där ett felaktigt orderdatum skrivs ut på PDF-fakturan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 är installerat. Korrigerings-ID är MDVA-30862. Observera att problemet har åtgärdats i Adobe Commerce 2.4.0.
exl-id: 695f530e-6abf-4883-972d-5d9c379493a2
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# MDVA-30862: Felaktigt orderdatum på utskriven PDF-faktura

MDVA-30862-korrigeringen åtgärdar ett problem där ett felaktigt orderdatum skrivs ut på PDF-fakturan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 har installerats. Korrigerings-ID är MDVA-30862. Observera att problemet har åtgärdats i Adobe Commerce 2.4.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.3.4

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.3.7-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Fel orderdatum skrivs ut på PDF-fakturan.

<u>Steg som ska återskapas</u>:

1. Gå till **Försäljning** > **Beställningar**.
1. Välj en order och skriv ut fakturan.

<u>Förväntade resultat</u>:

Datumet matchar inköpsdatumet.

<u>Faktiska resultat</u>:

Datumet (inklusive månad/år) matchar inte inköpsdatumet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
