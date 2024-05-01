---
title: "MDVA-32714 patch: kundgruppspriset fungerar inte via GraphQL'"
description: MDVA-32714-korrigeringen åtgärdar ett problem där с kundgruppspris inte läggs till i svaret på GraphQL produktfråga. Den här korrigeringen är tillgänglig när QPT (Quality Patches Tool) 1.0.13 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: a4fc92ad-68dc-437d-8577-303007ef8a92
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-32714-korrigering: kundgruppspriset fungerar inte via GraphQL

>[!WARNING]
>
>En ny patch som heter MDVA-33975 åtgärdar GraphQL problem med prisberäkning. MDVA-32714 är avskriven och vi rekommenderar att du använder MDVA-33975-patchen. Om du vill komma åt den här korrigeringen läser du [MDVA-33975-korrigering: GraphQL prisberäkningar](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html) i vår kunskapsbas för support.

MDVA-32714-korrigeringen åtgärdar ett problem där с kundgruppspris inte läggs till i svaret på GraphQL produktfråga. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.4.0

**Kompatibel med Adobe Commerce:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.4 - 2.4.0-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundgruppspris för den allmänna kunden läggs inte till i GraphQL produktfrågesvar.

<u>Steg som ska återskapas</u>:

1. Aktivera och ange specialpris för alla produkter för alla kundgrupper.
1. Använd produktfrågan i GraphQL för att höja priserna för den här produkten enligt beskrivningen i: [Frågor för produkter > Exempelfråga](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html#sample-queries) i vår dokumentation för utvecklare.

<u>Förväntade resultat</u>:

```api
price_range
```

visar det rabatterade priset för allmänna kunder enligt vad som har definierats på Admin Panel.

<u>Faktiska resultat</u>:

```api
price_range
```

visar inte det rabatterade priset för allmänna kunder.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
