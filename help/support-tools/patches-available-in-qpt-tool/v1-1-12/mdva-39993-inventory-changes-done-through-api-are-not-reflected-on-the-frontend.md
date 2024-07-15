---
title: 'MDVA-39993: Lagerändringar som görs via API återspeglas inte i storefront'
description: MDVA-39993-korrigeringen löser problemet där lagerändringar som görs via API inte syns i butiken. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-39993. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 2d49b9b7-8a70-44f3-80bf-4460bb2e61d5
feature: REST, Inventory, Orders, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# MDVA-39993: Lagerändringar som görs via API återspeglas inte i storefront

MDVA-39993-korrigeringen löser problemet där lagerändringar som görs via API inte syns i butiken. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-39993. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5 - 2.3.7-p2 och 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

De lagerändringar som görs via API återspeglas inte på butikens produktsida.

<u>Förutsättningar</u>:

Lagermoduler har installerats.

<u>Steg som ska återskapas</u>:

1. Kontrollera att kön är inställd på att köras med cron och cron är installerat och igång.
1. Skapa en konfigurerbar produkt (COC001) med två färger (svart och röd) och två storlekar (M och L).
1. Gör ett av lageralternativen (COC001-Red-M).
1. Läs in den konfigurerbara produktsidan i butiken och försök klicka på varje färg. När du klickar på **Röd** bör storleken **M** strykas över eftersom den inte finns i lager.
1. Gör COC001-Red-M i lager med följande API-slutpunkt och nyttolast:

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. Kontrollera den här enkla produkten från bakgrunden och verifiera att den har uppdaterats till In Stock.
1. Läs in den konfigurerbara produkten från förgrunden och klicka på varje färg. Lägg märke till storleken **M** när du klickar på **Röd**.

<u>Förväntade resultat</u>:

Alternativet COC001-Red-M stryks inte över eftersom det har uppdaterats till In Stock via API.

<u>Faktiska resultat</u>:

COC001-Red-M-alternativet stryks fortfarande, även om det är i Stock.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
