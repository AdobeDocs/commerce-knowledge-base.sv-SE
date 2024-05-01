---
title: 'MDVA-33559-korrigering: PayflowPro-betalningen nekade fel'
description: MDVA-33559-korrigeringen löser problemet där PayPal PayflowPro-betalningar nekas.
exl-id: aec57ffa-07c7-404e-985d-8ec4fdb019b1
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# MDVA-33559-korrigering: PayflowPro-betalningen nekade fel

MDVA-33559-korrigeringen löser problemet där PayPal PayflowPro-betalningar nekas.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 är installerat. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce:** Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Problemet gäller specialtecken för et-tecken (&amp;) och likhetstecken (=) som används i namn.

<u>Steg som ska återskapas</u>:

1. Lägg en enkel produkt i kundvagnen.
1. Gå till kassan.
1. Ange leveransadress. (Exempel på leveransadress: **Förnamn** = ** *John&#39;s* **  **Efternamn** = ** *Apples &amp; Oranges, Inc* **  **Gatuadress** = *1234E Namless St*  **Land** = *USA*  **Stat/provins** = *Anystate*  **Ort** = *Anytown*  **Postnummer** = *12345*  **Telefon** = *1234567890*)
1. Ställ in betalning till **PayPal PayflowPro** och försök att slutföra utcheckningen.

<u>Förväntade resultat</u>:

Transaktionen resulterar i en slutförd betalning eller ett korrekt felmeddelande, som förväntat.

<u>Faktiska resultat</u>:

Transaktionen avvisas och kunden får ett e-postmeddelande med texten&quot;Transaktionen har avböjts&quot;.

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
