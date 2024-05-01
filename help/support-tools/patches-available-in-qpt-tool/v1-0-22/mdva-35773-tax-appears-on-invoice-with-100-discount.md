---
title: 'MDVA-35773: Moms visas på faktura med 100 % rabatt'
description: MDVA-35773-korrigeringen åtgärdar problemet med att Totalsumman inte visas som noll på fakturan för order med 100 % rabatt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 är installerat. Patch-ID:t är MDVA-35773. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
exl-id: 895cb7d3-be9f-4864-9658-87ee0471f556
feature: Invoices, Marketing Tools, Orders, Personalization, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-35773: Moms visas på faktura med 100 % rabatt

MDVA-35773-korrigeringen åtgärdar problemet med att Totalsumman inte visas som noll på fakturan för order med 100 % rabatt. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 är installerat. Patch-ID:t är MDVA-35773. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.6

**Kompatibel med Adobe Commerce:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.6-2.3.7 och 2.4.1-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Navigera till **Lager** > **Inställningar** > **Konfiguration** > **Försäljning** > **Moms**.
1. Ange **Katalogpriser** och **Använd rabatt på priser** till *Inklusive skatt*.
1. Navigera till **Lager** > **Skatteregler** > **Lägg till ny momsregel**.
1. Skapa en momsregel (Exempel: alla USA med 10 % momssats) och tillämpa den.
1. Navigera till **Marknadsföring** > **Kundprisregler** och **Lägg till ny regel**.
1. Skapa en regel med en **100 % rabatt för alla användare**.
1. Gör en beställning på Storefront:

   * Välj **Fri frakt**.
   * Använd **Kupongkod**.

1. Navigera till **Försäljning** > **Beställningar** och öppna din beställning.
1. Skapa en faktura för ordern och öppna den.

<u>Förväntade resultat</u>:

Fakturans totalsumma = *$0,00*.

<u>Faktiska resultat</u>:

Fakturans totalsumma = *momsbelopp* skapas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
