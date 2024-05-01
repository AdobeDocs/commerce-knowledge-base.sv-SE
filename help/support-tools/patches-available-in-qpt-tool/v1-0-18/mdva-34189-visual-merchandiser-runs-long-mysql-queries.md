---
title: 'MDVA-34189: Visuell handlare kör långa MySQL-frågor'
description: MDVA-34189-korrigeringen löser problemet där Adobe Commerce kör stora visuella Merchandiser-frågor när sidan för Admin-kategorin läses in.
exl-id: 94143d80-3240-4a18-890d-fb759ea9c30d
feature: Categories, Merchandising, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-34189: Visuell handlare kör långa MySQL-frågor

MDVA-34189-korrigeringen löser problemet där Adobe Commerce kör stora visuella Merchandiser-frågor när sidan för Admin-kategorin läses in.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Korrigerings-ID är MDVA-34189. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce:** Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.4-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Webbplatsen kör stora MySQL-frågor på produktionsservern.

<u>Steg som ska återskapas</u>:

1. För att få åtkomst till Visual Merchandiser går du till *Administratör* sidlist, klicka **Katalog** > **Kategorier**.
1. Läs in **Kategorier** sidan på panelen Admin (den inledande rotkategorin inläst) och observera de frågor som den kör.

<u>Förväntat resultat</u>:

Administratören **Kategorier** sidan ska läsas in utan att långsamma frågor genereras.

<u>Faktiskt resultat</u>:

Detta beror på PHP-konfigurationen. Det vanligaste exemplet på det här felet är att **Kategorier** sidan öppnas inte och ett fel uppstår *Fel 503, timeout för första byte* visas.

När Adobe Commerce läser in Visual Merchandiser körs en långsam MySQL-fråga. Den här frågan innehåller många produkt-ID som infogats i `ORDER BY FIELD(`e`.`entity_id`,  ...)`

in `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
