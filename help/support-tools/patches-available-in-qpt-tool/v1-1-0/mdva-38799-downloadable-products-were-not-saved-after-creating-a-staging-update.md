---
title: 'MDVA-38799: Hämtningsbara produkter som inte sparats efter att en mellanlagringsuppdatering har skapats'
description: MDVA-38799-korrigeringen åtgärdar ett problem där hämtningsbara produkter inte sparas efter att en mellanlagringsuppdatering har skapats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 är installerat. Korrigerings-ID är MDVA-38799. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
exl-id: 306f9ef3-ca3a-41b9-a5d3-42aa4ef59953
feature: Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-38799: Hämtningsbara produkter som inte har sparats efter att en mellanlagringsuppdatering har skapats

MDVA-38799-korrigeringen åtgärdar ett problem där hämtningsbara produkter inte sparas efter att en mellanlagringsuppdatering har skapats. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 är installerat. Korrigerings-ID är MDVA-38799. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0-2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Hämtningsbara produkter sparas inte när en mellanlagringsuppdatering har skapats. Användarna får felmeddelandet: *Det hämtningsbara urvalet är inte relaterat till produkten. Kontrollera länken och försök igen*.

<u>Steg som ska återskapas</u>:

1. Navigera till **Katalog** > **Produkter**.
1. Klicka på listrutan bredvid Lägg till produkt och välj Hämtningsbar produkt.
   * Fyll i namn, SKU, pris och kvantitet för produkten.
1. Bläddra ned till sidan Hämtningsbar information.
1. Klicka på under Exempel **Lägg till länk**.
   * Fyll i rubriken Överför fil (filtypen spelar ingen roll).
1. Klicka **Spara**. Du får följande meddelande: *Du har sparat produkten*.
1. Klicka **Schemalägg ny uppdatering** överst på sidan.
   * Fyll i uppdateringsnamnet och ett giltigt startdatum och slutdatum.
1. Klicka **Spara** på mellanlagringsuppdateringen.
1. Klicka **Spara** på produkten.

<u>Förväntade resultat</u>:

Produkten sparas utan fel.

<u>Faktiska resultat</u>:

Felmeddelandet visas: *Det hämtningsbara urvalet är inte relaterat till produkten. Kontrollera länken och försök igen*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
