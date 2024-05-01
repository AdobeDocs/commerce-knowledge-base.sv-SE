---
title: 'MDVA-33289 patch: Javascript in address at checkout'
description: Korrigeringen MDVA-33289 åtgärdar problemet där Javascript visar adressen vid betalning. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Korrigerings-ID är MDVA-33289. Observera att problemet var planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 247e4f05-7e89-4d37-b3d4-c2cae7595267
feature: Checkout, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-33289-korrigering: Javascript in address at checkout

Korrigeringen MDVA-33289 åtgärdar problemet där Javascript visar adressen vid betalning. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Korrigerings-ID är MDVA-33289. Observera att problemet var planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce:** Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.4.0 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du checkar ut med Google Tag Manager (GTM) aktiverat visas Javascript i adressfältet.

<u>Steg som ska återskapas</u>:

1. Aktivera GTM. Se [Google Tag Manager](https://docs.magento.com/user-guide/marketing/google-tag-manager.html) i användarhandboken för mer information.
1. I butiken lägger du till några produkter i kundvagnen.
1. Kolla in.

<u>Faktiskt resultat</u>:

Adressavsnittet uppdateras, men innehåller mycket Javascript-kodtext.

<u>Förväntat resultat</u>:

Adress visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
