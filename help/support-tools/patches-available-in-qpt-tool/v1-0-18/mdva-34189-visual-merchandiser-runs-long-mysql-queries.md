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

Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Korrigerings-ID är MDVA-34189. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce lokalt och Adobe Commerce i molninfrastruktur 2.3.4-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Webbplatsen kör stora MySQL-frågor på produktionsservern.

<u>Steg som ska återskapas</u>:

1. Om du vill komma åt Visual Merchandiser går du till sidofältet *Admin* och klickar på **Katalog** > **Kategorier**.
1. Läs in sidan **Kategorier** på panelen Admin (inläsning av den inledande rotkategorin) och observera de frågor som den kör.

<u>Förväntat resultat</u>:

Sidan Admin **Kategorier** ska läsas in utan att långsamma frågor genereras.

<u>Faktiskt resultat</u>:

Detta beror på PHP-konfigurationen. Det vanligaste exemplet på det här felet är att sidan **Kategorier** inte öppnas och att ett fel *Fel 503 som timeout för första byte* visas.

När Adobe Commerce läser in Visual Merchandiser körs en långsam MySQL-fråga. Den här frågan innehåller många produkt-ID som infogats i `ORDER BY FIELD(`e`.`entity_id`,  ...)`

i `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
