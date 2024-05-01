---
title: "ACSD-45754: Belöningspoäng som inte lagts till efter kupong"
description: Korrigeringen ACSD-45754 löser problemet där belöningspoäng inte läggs till efter att en kupong har använts på vagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 är installerat. Korrigerings-ID är ACSD-45754. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: 957713c0-3e2e-4dc9-8924-2ae84c817e47
feature: Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-45754: Belöningspunkter har inte lagts till efter kupong

Korrigeringen ACSD-45754 löser problemet där belöningspoäng inte läggs till efter att en kupong har använts på vagnen. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 är installerat. Korrigerings-ID är ACSD-45754. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.1 - 2.4.5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Belöningspoäng läggs inte till efter att en kupong har använts i kundvagnen.

<u>Förutsättningar</u>:

Betalningsmetoden PayPal har konfigurerats.

<u>Steg som ska återskapas</u>:

1. Skapa valutakurser för belöningspunkter genom att gå vidare **Butik** > **Andra inställningar** > **Belöningsbaserade växelkurser**.
1. Skapa en kundvagnsprisregel med en kupongkod för att tillämpa 100 belöningspoäng för inloggade kunder.
1. Kolla in en produkt som inloggad kund med PayPal och kupongkoden.
1. Kontrollera belöningspunktshistoriken under kundkontot i administratören.

<u>Förväntade resultat</u>:

Belöningspoäng läggs till kunden enligt prisregeln.

<u>Faktiska resultat</u>:

Inga belöningspoäng läggs till kunden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
