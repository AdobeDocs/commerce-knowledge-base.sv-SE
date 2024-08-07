---
title: 'MDVA-35254: CAPTCHA-utcheckningen fungerar inte korrekt'
description: Korrigeringen MDVA-35254 åtgärdar ett problem med att CAPTCHA-fält inte visas efter ett misslyckat antal utcheckningsförsök för tredjepartsbetalning. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-35254. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
exl-id: 226c672b-3740-4a87-9ea1-66892acb9fe2
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-35254: CAPTCHA-utcheckning fungerar felaktigt

Korrigeringen MDVA-35254 åtgärdar ett problem med att CAPTCHA-fält inte visas efter ett misslyckat antal utcheckningsförsök för tredjepartsbetalning. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-35254. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.1-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

Konfigurera CAPTCHA:

1. Installera och konfigurera tredjepartsbetalningsleverantör (Exempel: Braintree).
1. Gå till **Store > Configuration > Customer Configuration > CAPTCHA > Forms**.
1. Välj **Utcheckning/Placeringsordning**.
1. Behåll **antalet misslyckade försök att logga in** som standard (standard = **).
1. Logga in som kund.
1. Lägg valfri produkt i kundvagnen.
1. Gå till betalningsavsnittet i kassan.
1. Välj betalningsmetod **Kreditkort** (Exempel: Braintree).
1. Gör tre misslyckade betalningsförsök.

<u>Förväntade resultat</u>:

Fältet CAPTCHA visas när antalet misslyckade försök har uppnåtts.

<u>Faktiska resultat</u>:

CAPTCHA-fältet visas aldrig, bara felmeddelandet: *Ange CAPTCHA-kod och försök igen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
