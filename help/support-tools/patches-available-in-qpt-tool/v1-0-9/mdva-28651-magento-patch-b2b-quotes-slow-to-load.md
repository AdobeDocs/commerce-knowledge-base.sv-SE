---
title: 'MDVA-28651: B2B - citattecken laddas långsamt'
description: MDVA-28651-korrigeringen åtgärdar ett problem där det uppstår flera prestandaproblem med laddningsofferter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9 är installerat. Observera att problemet var planerat att åtgärdas i Adobe Commerce version 2.4.2.
exl-id: 2d0bfbba-cdf3-4f9e-a900-ce42909fac8e
feature: B2B, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-28651: B2B - citattecknen är långsamma att läsa in

MDVA-28651-korrigeringen åtgärdar ett problem där det uppstår flera prestandaproblem med laddningsofferter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9 har installerats. Observera att problemet var planerat att åtgärdas i Adobe Commerce version 2.4.2.

## Berörda produkter och versioner

* Korrigeringen har utformats för Adobe Commerce i molninfrastruktur 2.3.4.
* Korrigeringen är även kompatibel med följande Adobe Commerce-versioner: Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.3.0-2.3.5-p1, 2.4.0 och 2.4.1.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Prestandaproblem på listsidan för kundofferter:

* Dubbel inläsning av offertlistan: första med hela sidan, andra med Ajax-begäran.
* en slinga som läser in citattecknen från plugin-programmet.
* dubbelinläsning av offertobjekt när offerten konverterades till ögonblicksbilden.

<u>Steg som ska återskapas</u>

1. Har fler än 40 citattecken tilldelade till en kund.
1. Logga in och bläddra på sidan **Mina offerter**.

<u>Faktiskt resultat</u>

Svarstiden för fullständig inläsning av innehållet på sidan **Mina citattecken** (inläsning av sidan + data som visas i rutnätet) är ~ 45 sekunder.

<u>Förväntat resultat</u>

Svarstiden för fullständig inläsning av innehållet på sidan **Mina citattecken** måste vara mindre än 45 sekunder.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
