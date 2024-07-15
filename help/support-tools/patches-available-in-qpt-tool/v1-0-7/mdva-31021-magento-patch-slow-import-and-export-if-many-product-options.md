---
title: 'MDVA-31021: långsam import och export om många produktalternativ finns'
description: MDVA-31021-korrigeringen löser problemet när import/export tar längre tid än förväntat med ett stort antal produktalternativ. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat.
exl-id: d294b30d-b734-4bd6-bf1a-c116b789a63c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-31021: långsam import och export om det finns många produktalternativ

MDVA-31021-korrigeringen löser problemet när import/export tar längre tid än förväntat med ett stort antal produktalternativ. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce i molninfrastruktur 2.3.1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om det finns minst 100 000 poster i tabellen `catalog_product_option` tar valideringen av import-/exportfunktionsfilen längre tid än förväntat. Före import/export, för att kontrollera validering av alternativ, läser Adobe Commerce in produktalternativ för alla befintliga produkter.

<u>Förutsättningar</u>:

Adobe Commerce Store med 5000 produkter med anpassade alternativ. Varje produkt bör ha minst fyra anpassade alternativ med två eller flera alternativ att välja mellan så att det finns 100 000 poster i tabellen `catalog_product_option`.

<u>Steg som ska återskapas</u>:

1. För ett **importexempel**: skapa en CSV-importfil med en av SKU:erna från Commerce Admin.
1. Lägg till fyra anpassade alternativ i CSV-importfilen.
1. Försök att importera CSV-filen från Commerce Admin.

<u>Förväntade resultat</u>:

Funktionen Importera eller Exportera slutförs som förväntat. Valideringen tar mindre än 10 sekunder att slutföra med en produkt.

<u>Faktiska resultat</u>:

Funktionen Importera eller Exportera tar längre tid än förväntat. Valideringen tar mer än 10 sekunder att slutföra med endast en produkt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
