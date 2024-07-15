---
title: 'MDVA-38308: Fel när Vimeo-videor lades till i inaktiverade produkter'
description: "MDVA-38308 quality patch for Adobe Commerce löser problemet där användare får felmeddelandet: *Obs! Odefinierat index: extension in /lib/internal/Magento/Framework/File/Uploader.php on line 806,* när de lägger till Vimeo-videor i inaktiverade produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 är installerat. Patch-ID:t är MDVA-38308. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4."
exl-id: ed5fb9ec-c465-4bb9-8a29-4d5e4bd4c867
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-38308: Fel när Vimeo-videofilmer lades till i inaktiverade produkter

MDVA-38308-kvalitetskorrigeringen för Adobe Commerce löser problemet där användarna får felmeddelandet: *Obs! Odefinierat index: extension in /lib/internal/Magento/Framework/File/Uploader.php on line 806,* när Vimeo-videor läggs till i inaktiverade produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 är installerat. Patch-ID:t är MDVA-38308. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
Adobe Commerce om molninfrastruktur 2.4.1-p1, 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**
Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.5 - 2.3.6-p1, 2.4.0 - 2.4.1-p1, 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du lägger till Vimeo-videofilmer i inaktiverade produkter får du följande felmeddelande: *Obs! Odefinierat index: extension in /lib/internal/Magento/Framework/File/Uploader.php on line 806*

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Inaktivera den skapade produkten.
1. Försök lägga till en Vimeo-video i den inaktiverade produkten.

<u>Förväntade resultat</u>:

Video läggs till utan fel.

<u>Faktiska resultat</u>:

Du får följande fel:
*Obs! Odefinierat index: tillägg i /lib/internal/Magento/Framework/File/Uploader.php på rad 806*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal Adobe Commerce: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html)

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar i vår kunskapsbas finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Mer information om andra korrigeringsfiler som är tillgängliga i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) i vår supportkunskapsbas.
