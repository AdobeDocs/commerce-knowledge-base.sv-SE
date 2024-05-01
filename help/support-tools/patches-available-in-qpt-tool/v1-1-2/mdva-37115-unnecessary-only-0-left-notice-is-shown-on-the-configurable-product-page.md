---
title: '"MDVA-37115: Meddelandet "Endast 0 kvar" visas på produktsidan'
description: MDVA-37115-korrigeringen åtgärdar ett problem där det onödiga *Endast 0 varningar* visas på den konfigurerbara produktsidan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-37115. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 08aa6ac7-13ae-44c1-9db4-d449c3d8c985
feature: Configuration, Products, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# MDVA-37115: Meddelandet &quot;Endast 0 kvar&quot; visas på produktsidan

MDVA-37115-korrigeringen löser problemet där den onödiga *Endast 0 kvar* visas på den konfigurerbara produktsidan. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-37115. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionstyper) 2.4.2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionstyper) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Onödigt *Endast 0 kvar* visas på den konfigurerbara produktsidan.

<u>Förutsättningar</u>:

Lagermoduler är installerade.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med få alternativ.
1. Gå till fronten.
1. Öppna den konfigurerbara produktsidan och välj ett alternativ.

<u>Förväntade resultat</u>:

Nej *Endast 0 kvar* visas på produktsidan.

<u>Faktiska resultat</u>:

*Endast 0 kvar* visas på produktsidan.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) -avsnitt.
