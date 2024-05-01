---
title: 'MDVA-31519-korrigering: förlorad order efter gästutcheckning'
description: MDVA-31519-korrigeringen löser problemet där betalda order saknas och låser timeout vid gästutcheckning.
exl-id: 2b4f9992-d58d-434f-adf8-d8ad8f761755
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# MDVA-31519-korrigering: förlorad ordning efter gästutcheckning

MDVA-31519-korrigeringen löser problemet där betalda order saknas och låser timeout vid gästutcheckning.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 är installerat. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce:**

Adobe Commerce om molninfrastruktur och Adobe Commerce lokalt 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Aktivera gästutcheckning.
1. Skapa en kundvagnsprisregel utan kupong (Exempel:&quot;Fri frakt över x belopp&quot;).
1. Lägg en stor mängd samtidiga gästorder med API-betaltjänstleverantörer (PSP).

<u>Förväntade resultat</u>:

Alla betalda betalningstransaktioner sparas i databasen och visas i administratören, som förväntat.

<u>Faktiska resultat</u>:

Endast en liten del av beställningarna sparas i databasen, medan större delen av beställningens information går förlorad på grund av timeout för låsväntetider.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
