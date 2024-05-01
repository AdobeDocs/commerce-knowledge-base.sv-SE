---
title: "MDVA-30428: önskelistan fungerar inte med Inventory management"
description: MDVA-30428-korrigeringen löser önskelistan som inte fungerar med Inventory management (MSI). Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat.
exl-id: 79e8d5d6-b073-48cf-8ecc-5c44667c12ad
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-30428: önskelistan fungerar inte med Inventory management

MDVA-30428-korrigeringen löser önskelistan som inte fungerar med Inventory management (MSI). Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3 - 2.3.3-p1 (QPT 1.0.6) och 2.3.5 - 2.4.1 (QPT 1.0.5)

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du lägger till en produkt i önskelistan visas följande meddelande när produkten tilldelas en anpassad lagerkälla:*Det går inte att lägga till objektet i önskelistan just nu: Det går inte att lägga till produkten utan arkiv i önskelistan.*&quot;

<u>Steg som ska återskapas</u>:

1. Skapa en ny lagerkälla i Commerce Admin. Om du vill se steg går du till [Katalog > Lägga till en ny källa](https://docs.magento.com/user-guide/catalog/inventory-sources-add.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=new%20inventory%20source) i vår användarhandbok.
1. Skapa ett nytt lagerlager i Commerce Admin, tilldela den nya källan och standardwebbplatsen till det nya lagret. Om du vill se steg går du till [Katalog > Lägga till ett nytt Stock](https://docs.magento.com/user-guide/catalog/inventory-stock-add.html#add-new-stock) i vår användarhandbok.
1. Skapa en enkel produkt och tilldela bara det nya lagret som lager.
1. Besök den enkla produktinformationssidan i förgrunden.
1. Lägg till produkten i önskelistan. Följande fel visar: *Det går inte att lägga till objektet i önskelistan just nu: Det går inte att lägga till produkten utan arkiv i önskelistan*.

<u>Förväntade resultat</u>:

Produkten bör läggas till i önskelistan med det anpassade lagret.

<u>Faktiska resultat</u>:

Produkten läggs inte till i önskelistan och ett felmeddelande visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
