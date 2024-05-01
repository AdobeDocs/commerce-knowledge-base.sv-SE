---
title: 'MDVA-40545: Endast den första noden för en sida hämtas'
description: MDVA-40545-korrigeringen löser problemet där bara den första noden för en sida hämtas, även om det finns mer än en nod för samma sida. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 är installerat. Korrigerings-ID är MDVA-40545. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: ac7aaed9-5e81-45fe-b699-40d9c086a05c
feature: CMS, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-40545: Endast den första noden för en sida hämtas

MDVA-40545-korrigeringen löser problemet där bara den första noden för en sida hämtas, även om det finns mer än en nod för samma sida. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 är installerat. Korrigerings-ID är MDVA-40545. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Endast den första noden för en sida hämtas, även om det finns mer än en nod för samma sida.

<u>Steg som ska återskapas</u>:

1. Gå till panelen Admin **Hierarki** och lägga till två menyalternativ/noder.
1. Lägg till samma CMS-sida för varje nod.
1. Rensa cacheminnet och kontrollera frontend.
1. Kontrollera länkar och vägbeskrivningar för den första tillagda undermenyn.
1. Kontrollera länkar och vägbeskrivningar för den andra tillagda undermenyn.

<u>Förväntade resultat</u>:

Brödkrummar och länkar på den andra undermenyn är relevanta för den andra noden.

<u>Faktiska resultat</u>:

Brevlådor och länkar på den andra undermenyn är samma som den första undermenyn.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) -avsnitt.
