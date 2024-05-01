---
title: 'MDVA-38929: Fakturan med FPT visar fel summa'
description: MDVA-38929-korrigeringen löser problemet där fakturan med FPT visar en felaktig totalsumma när ordern betalas med butikskrediter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-38929. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 1ed0e311-f4a5-4dc0-98fc-fc1cc9458516
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-38929: Fakturan med FPT visar fel summa

MDVA-38929-korrigeringen löser problemet där fakturan med FPT visar en felaktig totalsumma när ordern betalas med butikskrediter. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-38929. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Fakturan med FPT visar en felaktig totalsumma när ordern betalas med butikskrediter.

<u>Steg som ska återskapas</u>:

1. Skapa en kund och se till att kunden har butikskrediter som täcker ordern.
1. Aktivera FPT och lägg till FPT i en produkt.
1. Logga in direkt när kunden just har skapat.
1. Lägg produkten med FPT i kundvagnen.
1. Checka ut och betala med butikskrediter. Det ska vara en nolllöneorder.
1. Gå till Beställningar och fakturera ordern manuellt.
1. Kontrollera totalsumman för fakturan.

<u>Förväntade resultat</u>:

* Fakturans totalsumma är noll.
* Det totala betalda orderbeloppet är noll.

<u>Faktiska resultat</u>:

* Fakturans totalsumma visar fortfarande FPT-beloppet.
* Det totala betalda beloppet visar fortfarande beloppet för bildrutorna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
