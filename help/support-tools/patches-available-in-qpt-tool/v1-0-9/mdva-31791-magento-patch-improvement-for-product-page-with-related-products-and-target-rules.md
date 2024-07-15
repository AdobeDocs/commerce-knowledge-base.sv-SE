---
title: 'MDVA-31791 patch: förbättring för produktsida med relaterade produkter och målregler'
description: MDVA-31791-korrigeringen förbättrar prestandan för produktsidor när [Relaterade produkter](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) eller [Relaterade produkter, regler](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (målregler) används. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.1.
exl-id: e737bccb-d9eb-4794-9d6b-2c22fa8edaa2
feature: Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-31791-korrigering: Förbättring för produktsida med relaterade produkter och målregler

MDVA-31791-korrigeringen förbättrar prestandan för produktsidor när [relaterade produkter](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) eller [relaterade produktregler](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (målregler) används. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.1.

## Berörda produkter och versioner

**Korrigeringen skapades för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.4.0

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce om molninfrastruktur och Adobe Commerce lokalt 2.3.4, 2.3.4-p1, 2.3.4-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Låga prestanda för produktsidor om relaterade produkter eller Target-regler används.

Överväg att använda MDVA-31791-korrigeringsfilen om du ska använda funktionen [Relaterad produkt](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) eller [Relaterade produktregler](https://docs.magento.com/user-guide/marketing/product-related-rules.html).

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [korrigeringsfilerna i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
