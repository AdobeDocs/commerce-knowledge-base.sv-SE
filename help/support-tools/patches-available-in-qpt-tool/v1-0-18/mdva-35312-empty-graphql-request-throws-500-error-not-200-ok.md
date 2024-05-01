---
title: 'MDVA-35312: tom GraphQL-begäran orsakar 500-fel och inte 200 OK'
description: Korrigeringen MDVA-35312 åtgärdar ett problem där en tom GraphQL-begäran orsakar felsvarskod 500. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Korrigerings-ID är MDVA-35312. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 345fdbd4-8a43-4aab-a318-72792c8a7a78
feature: GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# MDVA-35312: tom GraphQL-begäran ger 500-fel och inte 200 OK

Korrigeringen MDVA-35312 åtgärdar ett problem där en tom GraphQL-begäran orsakar felsvarskod 500. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Korrigerings-ID är MDVA-35312. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Magento-versionen:**

Adobe Commerce i molninfrastruktur 2.4.2

**Kompatibel med Magento-versioner:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.4.1-p1-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Tom GraphQL-begäran ger felsvarskod 500 i stället för 200.

<u>Steg som ska återskapas</u>:

Skicka en GraphQL-förfrågan, till exempel:

```curl
curl -i -X OPTIONS http://inv.test/graphql
```

<u>Förväntade resultat</u>:

Svar: *200 OK*.

<u>Faktiska resultat</u>:

Svar: *HTTP/1.1 500 Internt serverfel*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
