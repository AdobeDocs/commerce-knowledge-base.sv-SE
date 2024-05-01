---
title: "MDVA-22150 Adobe Commerce patch: frontanvändare kan inte logga in"
description: MDVA-22150-korrigeringen löser problemet när en kund inte kan logga in efter ett avbrutet köp med en kupong. Detta inträffar när en kund använder en kupongkod på en produkt som har inaktiverats innan köpet slutfördes. Resultatet är att klientanvändaren inte längre kan logga in och får ett 503-fel. En annan effekt av det här problemet är att möjligheten att hantera kundens kundvagnar i administratören slutar att fungera.
exl-id: 8aabe7b2-4b8a-4339-914e-7131006907b3
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# MDVA-22150 Adobe Commerce-patch: frontanvändare kan inte logga in

MDVA-22150-korrigeringen löser problemet när en kund inte kan logga in efter ett avbrutet köp med en kupong. Detta inträffar när en kund använder en kupongkod på en produkt som har inaktiverats innan köpet slutfördes. Resultatet är att klientanvändaren inte längre kan logga in och får ett 503-fel. En annan effekt av det här problemet är att möjligheten att hantera kundens kundvagnar i administratören slutar att fungera.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.3.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce om molninfrastruktur 2.3.2

**Kompatibel med Adobe Commerce:** Adobe Commerce om molninfrastruktur och Adobe Commerce 2.3.1 - 2.3.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas:</u>

1. Logga in på Admin och skapa en konfigurerbar produkt.
1. Gå till **Kundregler** och skapa en kupongkod med lite rabatt.
1. Skapa ett kundkonto i förgrunden.
1. Lägg produkten i kundvagnen, följ utcheckningsprocessen och ange kupongen.
1. När du har angett kupongen ska du inte skicka beställningen, utan avbryta beställningen och utloggningen.
1. Gå tillbaka till Admin och inaktivera hela den konfigurerbara produkten.

<u>Förväntade resultat:</u>

Produkten visas inte i varukorgen på Storefront eller med ett felmeddelande om att produkten har inaktiverats som förväntat.

<u>Faktiska resultat:</u>

* När du försöker logga in på fronten igen kommer du att fastna i en oändlig slinga (som efter en lång tid kommer att visa ett undantag).
* Möjligheten att hantera kundens kundvagnar i Admin slutar att fungera.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) -avsnitt.
