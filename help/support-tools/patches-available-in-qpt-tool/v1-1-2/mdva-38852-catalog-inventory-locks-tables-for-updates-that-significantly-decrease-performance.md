---
title: 'MDVA-38852: Kataloglager låser tabeller som försämrar prestanda'
description: MDVA-38852-korrigeringen löser problemet där kataloginventeringen låser tabeller för uppdateringar som avsevärt försämrar prestanda när flera parallella order placeras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Patch-ID:t är MDVA-38852. Observera att problemet har åtgärdats i Adobe Commerce 2.3.6.
exl-id: 6ecee9c8-1f39-47de-8fbc-55e30cc936af
feature: Catalog Management, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-38852: Kataloglager låser tabeller som minskar prestanda

MDVA-38852-korrigeringen löser problemet där kataloginventeringen låser tabeller för uppdateringar som avsevärt försämrar prestanda när flera parallella order placeras. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Patch-ID:t är MDVA-38852. Observera att problemet har åtgärdats i Adobe Commerce 2.3.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kataloglager låser tabeller för uppdateringar som avsevärt försämrar prestanda när flera parallella order placeras.

<u>Steg som ska återskapas</u>:

1. Lägg en produkt i kundvagnen.
1. Gå till kassan och försök att göra en beställning.

<u>Förväntade resultat</u>:

* Det finns inga dödlägen.
* Prestandan minskar inte om flera parallella order placeras.

<u>Faktiska resultat</u>:

* Att lägga en order är extremt långsamt när det finns flera samtidiga användare.
* Deadlock-fel inträffar som ser ut så här:

```SQL
"SQLSTATE[40001]: Serialization failure: 1213 Deadlock found when trying to get lock; try restarting transaction, query was:
INSERT INTO `quote_payment` (`quote_id`, `method`, `additional_information`) VALUES (?, ?, ?)"
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
