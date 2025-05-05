---
title: 'MDVA-40101: Objekten blir kvar i minikorgen efter beställningens PayPal Express Checkout'
description: Korrigeringen MDVA-40101 åtgärdar ett problem där objekt inte tas bort från minivagnen efter en lyckad beställningsmontering med PayPal Express Checkout. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 är installerat. Korrigerings-ID är MDVA-40101. Observera att problemet har åtgärdats i Adobe Commerce 2.4.0.
exl-id: d640dfcd-6fb6-4cc6-8817-3ae19aa59bed
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-40101: Objekten blir kvar i minikorgen efter beställningens PayPal Express Checkout

Korrigeringen MDVA-40101 åtgärdar ett problem där objekt inte tas bort från minivagnen efter en lyckad beställningsmontering med PayPal Express Checkout. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 har installerats. Korrigerings-ID är MDVA-40101. Observera att problemet har åtgärdats i Adobe Commerce 2.4.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.3.7

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Objekten finns kvar i minivagnen även efter en genomförd beställningsmontering med PayPal Express Checkout.

<u>Steg som ska återskapas</u>:

Gör en beställning med PayPal Express Checkout i Incognito-läge i en webbläsare.

<u>Förväntade resultat</u>:

Mini-cart ska vara tom när ordern har slutförts.

<u>Faktiska resultat</u>:

* På framgångssidan visas en tom minikundvagn.
* På alla andra sidor visas minikundvagn med inköpta artiklar.
* Om du klickar på kundvagnslänken dirigeras du om till en tom kundvagnssida.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
