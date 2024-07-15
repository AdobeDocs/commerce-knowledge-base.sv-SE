---
title: 'MDVA-37984: Visual Merchandiser fungerar inte korrekt när mellanlagringsuppdateringar tillämpas'
description: MDVA-37984-korrigeringen löser problemet där Visual Merchandisers"Match product by rule"-funktion inte filtrerar produkter korrekt när mellanlagringsuppdateringar tillämpas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 är installerat. Patch-ID:t är MDVA-37984. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984: Visual Merchandiser fungerar inte korrekt när mellanlagringsuppdateringar tillämpas

MDVA-37984-korrigeringen löser problemet där Visual Merchandisers&quot;Match product by rule&quot;-funktion inte filtrerar produkter korrekt när mellanlagringsuppdateringar tillämpas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 har installerats. Patch-ID:t är MDVA-37984. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Visual Merchandisers&quot;Match product by rule&quot;-funktion filtrerar inte produkter korrekt när mellanlagringsuppdateringar tillämpas.

<u>Steg som ska återskapas</u>:

1. Skapa en schemauppdatering för alla befintliga produkter.
   * Ange olika värden för `entity_id` och `row_id`.
1. Skapa en ny konfigurerbar produkt och sedan en enkel produkt (så den nya produkten `entity_id` och `row_ids` är också olika).
   * För att det ska bli enklare att replikera problemet anger du ett särskiljande värde för kvantitet för den enkla produkten, till exempel 5000.
1. Gå till en kategori > **Produkter i kategori** och aktivera **Matcha produkter efter regel**.
1. Välj sedan&quot;Quantity&quot; som attribut,&quot;Greater&quot; som operator och&quot;4500&quot; som värde.
1. Klicka på **Spara**.

<u>Förväntade resultat</u>:

Den nya konfigurerbara produkten visas.

<u>Faktiska resultat</u>:

Den nya konfigurerbara produkten visas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
