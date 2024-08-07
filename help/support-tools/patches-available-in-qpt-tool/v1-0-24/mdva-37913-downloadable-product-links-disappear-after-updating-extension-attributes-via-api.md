---
title: 'MDVA-37913: Länkar för nedladdning av produkter försvinner när tilläggsattribut har uppdaterats via API'
description: MDVA-37913-korrigeringen åtgärdar ett problem där de hämtningsbara produktlänkarna försvinner efter att tilläggsattributen uppdaterats via API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 är installerat. Korrigerings-ID är MDVA-37913. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: e4b2cf59-5c35-4a28-a63e-15cd7d0d5a5d
feature: REST, Attributes, Extensions, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-37913: Länkar för produktnedladdning försvinner när tilläggsattribut har uppdaterats via API

MDVA-37913-korrigeringen åtgärdar ett problem där de hämtningsbara produktlänkarna försvinner efter att tilläggsattributen uppdaterats via API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 är installerat. Korrigerings-ID är MDVA-37913. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.


## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
Adobe Commerce om molninfrastruktur 2.3.6

**Kompatibel med Adobe Commerce-versioner:**
Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.0 - 2.4.0-p1
>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.


## Problem

Hämtningsbara produktlänkar försvinner när du har uppdaterat tilläggsattribut via API.

<u>Förutsättningar</u>:
Nedladdningsbar produkt med nedladdningslänkar.

<u>Steg som ska återskapas</u>:

1. Uppdatera tilläggsattribut med en sådan begäran:

```JSON
{
    "product": {
        "extension_attributes": {
            "stock_item": {
                "is_in_stock": true,
                "qty": 100
            }
        }
    }
}
```

<u>Förväntade resultat</u>:<br>
Produkten har uppdaterats, alla nedladdningslänkar har inte tagits bort.

<u>Faktiska resultat</u>:<br>
Produkten har uppdaterats, men alla nedladdningslänkar har tagits bort.


## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal Adobe Commerce: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html)

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar i vår kunskapsbas finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Mer information om andra korrigeringsfiler som är tillgängliga i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) i vår supportkunskapsbas.
