---
title: "MDVA-37725: E-postmeddelanden som skickas via icke-standardwebbplatser innehåller standardwebbplatsens URL:er för logotyp"
description: Korrigeringen MDVA-37725 åtgärdar ett problem där asynkrona e-postmeddelanden om beställningar skickas via icke-standardwebbplatser som innehåller URL:er för logotyper från standardwebbplatsen.
exl-id: c0d1b9a3-01bb-445b-b7da-f9be6952eaeb
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-37725: E-postmeddelanden som skickas via icke-standardwebbplatser innehåller standardwebbplatsens logotyp-URL

>[!WARNING]
>
> MDVA-37725-korrigeringen är föråldrad.

Korrigeringen MDVA-37725 åtgärdar ett problem där asynkrona e-postmeddelanden om beställningar skickas via icke-standardwebbplatser som innehåller URL:er för logotyper från standardwebbplatsen. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 är installerat. Patch-ID:t är MDVA-37725. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Asynkrona e-postmeddelanden om beställning skickas via icke-standardwebbplatser som innehåller standardwebbplatsens logotyp-URL:er.

<u>Förutsättningar</u>:

1. Den andra webbplatsen/butiken/butiksvyn måste ha skapats.
1. **Asynkron sändning** konfiguration måste aktiveras från **Lager** > **Inställningar** > **Konfiguration** > **Försäljning** > **E-postadress** > **Allmänna inställningar**.
1. **Lägg till butikskod i URL:er** så att du enkelt kommer åt den sekundära webbplatsen från **Lager** > **Inställningar** > **Konfiguration** > **URL-alternativ**.

<u>Steg som ska återskapas</u>:

1. Lägg order från både den första och den andra butiken.
1. Kör cron för att skicka e-postmeddelanden.
1. Kontrollera e-postmeddelandet från den andra webbplatsen.

<u>Förväntade resultat</u>:

E-postens logotyp-URL innehåller den andra webbplatsens URL.

<u>Faktiska resultat</u>:

E-postens logotyp-URL innehåller standardwebbplatsens URL.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
