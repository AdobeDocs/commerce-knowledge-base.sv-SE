---
title: 'MDVA-34469: Felaktig butikskod har angetts för kundvagnen'
description: "MDVA-34469-korrigeringen löser problemet där användaren får felmeddelandet: *Felaktig butikskod angiven för kundvagn* när en produkt läggs till i kundvagnen efter att butiksvyn har växlats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 är installerat. Korrigerings-ID är MDVA-34469. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2."
exl-id: 35d4f120-7fcf-4996-8b23-aca99cfc18ac
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-34469: Felaktig butikskod har angetts för kundvagnen

MDVA-34469-korrigeringen löser problemet där användaren får felmeddelandet: *Fel butikskod har angetts för vagn* när du lägger till en produkt i kundvagnen efter att du har växlat mellan butiksvyer. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 är installerat. Korrigerings-ID är MDVA-34469. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce:**

Adobe Commerce om molninfrastruktur och Adobe Commerce lokalt 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren ser ett kundvagnsfrågefel, *&quot;Fel butikskod har angetts för kundvagn&quot;* när du försöker växla mellan butiksvyer.

<u>Förutsättningar</u>:

* Adobe Commerce 2.4.0.
* En webbplats med en enda butik och två butiksvyer är konfigurerade.
* Ett kundkonto skapas.

<u>Steg som ska återskapas</u>:

1. Adobe Commerce backend är konfigurerat att ha två butiksvyer (med butikskoder: standard, sekund).
1. Användaren skapar en kundvagn med standardbutikskoden.
1. Användaren försöker hämta den här vagnen med hjälp av den andra butikskoden i `Store` begäranhuvud.

<u>Förväntade resultat</u>:

Kundvagnen visas eftersom butiken byts ut (den nya koden skickas i `Store` begäranhuvud) associerar vagnen med det begärda arkivet.

<u>Faktiska resultat</u>:

Kundvagnsfrågan returnerar ett fel och vagnen visas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
