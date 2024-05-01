---
title: "MDVA-42584: Stock-status för konfigurerbar produkt uppdateras inte automatiskt"
description: MDVA-42584-korrigeringen löser problemet där den konfigurerbara produktens Stock-status inte uppdateras automatiskt när den enkla produkten uppdateras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Patch-ID:t är MDVA-42584. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584: Stock-status för konfigurerbar produkt uppdateras inte automatiskt

MDVA-42584-korrigeringen löser problemet där den konfigurerbara produktens Stock-status inte uppdateras automatiskt när den enkla produkten uppdateras. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Patch-ID:t är MDVA-42584. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerstatus för den konfigurerbara produkten i backend uppdateras inte automatiskt när dess enkla produkt är inställd på **I Stock** via API eller import.

<u>Förutsättningar</u>:

MSI har installerats.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt, **InvCheck001**, med två alternativ: **InvCheck001-M** och **InvCheck001-L**.
1. Båda de enkla produkterna ska ha Kvantitet och de ska vara **I Stock** så att den konfigurerbara produkten också **I Stock** i serverdelen.
1. Uppdatera nu både enkla produkter och ange Kvantitet till **0** och Stock-status till **Slut på lager**.
1. Uppdatera den konfigurerbara produkten och verifiera att Stock-statusen har uppdaterats till **Slut på lager**.
1. Använd följande API-slutpunkt och ställ in den enkla produkten **InvCheck001-M** till **I Stock** med Antal > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Gå till backend och verifiera den enkla produktens kvantitet och lagerstatus **InvCheck001-M**. Den uppdateras till **I lager**.
1. Uppdatera den konfigurerbara produkten och kontrollera lagerstatusen.

<u>Förväntade resultat</u>:

Lagerstatus för den konfigurerbara produkten **InvCheck001** i backend uppdateras automatiskt till **I Stock**.

<u>Faktiska resultat</u>:

Lagerstatusen för den konfigurerbara produkten är fortfarande **Slut på lager**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
