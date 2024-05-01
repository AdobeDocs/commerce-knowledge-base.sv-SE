---
title: 'MDVA-33482 patch: momsfelberäkning i kreditnota'
description: MDVA-33482-korrigeringen åtgärdar ett problem där moms beräknas felaktigt på kreditnotor.
exl-id: 80740e6f-2b6c-4770-9a1a-58ba68a1b28f
feature: Orders, Returns, Taxes
role: Admin
source-git-commit: 0ffa6d63f7046048f7e8f0e9fab1ee1869c98e93
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-33482-korrigering: Momsfelberäkning i kreditnota

MDVA-33482-korrigeringen åtgärdar ett problem där moms beräknas felaktigt i kreditnotor när ingen justerings- eller justeringsavgift används.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 är installerat. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce om molninfrastruktur 2.4.0

**Kompatibel med Adobe Commerce:** Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.5 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Konfigurera **Skatter**.
1. Skapa en beställning med två produkter i backend-serien med valfri onlinebetalningsmetod (Exempel: [!DNL PayPal Payment Pro]). Se till att moms tillämpas på alla produkter.
1. Skapa två fakturor för ordern.
1. Skapa en kreditnota mot en av fakturorna. Observera att lösningen inte är tillämplig om du planerar att använda en justeringsavgift eller ett justeringsbidrag.
1. Kontrollera kreditfakturasummor.

<u>Förväntade resultat</u>:

Endast ett delvis fakturerat momsbelopp finns i kreditnotan, som förväntat.

<u>Faktiska resultat</u>:

Det fullständiga momsbeloppet visas i kreditnotan.

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
