---
title: 'MDVA-40175: Alternativknappar visas inte vid omordning'
description: MDVA-40175-korrigeringen löser problemet där alternativknapparna inte visas när användaren försöker ändra ordningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Korrigerings-ID är MDVA-40175. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 307c450d-9f53-40b7-b2f5-d867850c043a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40175: Alternativknappar visas inte när ordningen ändras

MDVA-40175-korrigeringen löser problemet där alternativknapparna inte visas när användaren försöker ändra ordningen. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Korrigerings-ID är MDVA-40175. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Alternativknappar visas inte i avsnittet Betalnings- och leveransinformation när användare försöker beställa om.

<u>Förutsättningar</u>:

1. Ett kundkonto med en leveransadress och en faktureringsadress skapas.
1. En enkel produkt skapas.
1. Flera leveransmetoder har konfigurerats.
1. Minst en order skapas.

<u>Steg som ska återskapas</u>:

1. Gå till administrationspanelen > **Försäljning** > **Beställningar**.
1. Markera den skapade ordern.
1. Klicka på **Visa** länk.
1. Klicka på **Ändra ordning** -knappen.
1. Bläddra nedåt på sidan till sidan **Betalnings- och leveransinformation** -avsnitt.
1. Klicka på **Klicka för att ändra leveranssätt**.

<u>Förväntade resultat</u>:

Listan med leveransmetoder med alternativknappar visas.

<u>Faktiska resultat</u>:

Listan med leveransmetoder utan alternativknappar visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
