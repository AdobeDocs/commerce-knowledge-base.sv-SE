---
title: 'MDVA-43601: Utlösare tas bort från tabellen "catalogrle_product_price" efter fullständig indexering'
description: Korrigeringen MDVA-43601 åtgärdar ett problem där utlösare tas bort från tabellen "catalogrle_product_price" efter en fullständig indexering av "catalogrle_rule" eller "catalogrle_product". Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-43601. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601: Utlösare tas bort från tabellen &quot;catalogrle_product_price&quot; efter fullständig indexering

Korrigeringen MDVA-43601 åtgärdar ett problem där utlösare tas bort från tabellen `catalogrule_product_price` efter en fullständig indexering av `catalogrule_rule` eller `catalogrule_product`. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-43601. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Utlösare tas bort från tabellen `catalogrule_product_price` efter en fullständig omindexering av `catalogrule_rule` eller `catalogrule_product`.

<u>Steg som ska återskapas</u>:

1. Ställ in alla indexerare till *Uppdatera enligt schema*.
1. Kontrollera utlösarna som har skapats för tabellen `catalogrule_product_price` genom att köra följande SQL-begäran:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Indexera om `catalogrule_rule` eller `catalogrule_product` manuellt med följande kommando: `bin/magento indexer:reindex catalogrule_rule`
1. Kontrollera utlösarna för tabellen `catalogrule_product_price` igen.

<u>Förväntade resultat</u>:

Utlösare i tabellen `catalogrule_product_price` bevaras efter en fullständig omindexering.

<u>Faktiska resultat</u>:

Inga utlösare hittades för tabellen `catalogrule_product_price`.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
