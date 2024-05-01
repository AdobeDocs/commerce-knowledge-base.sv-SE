---
title: '"ACSD-51857: Det långsamma kronjobbet för "aggregat_sales_report_bestsellers_data" påverkar prestandan."'
description: Använd patchen ACSD-51857 för att åtgärda Adobe Commerce-problemet där långsamma cron-jobb "aggregate_sales_report_bestsellers_data" påverkar stora databastabeller av typen "sales_order" och "sales_order_item".
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857: Långsam kronjobb för `aggregate_sales_report_bestsellers_data` påverkar prestanda

Korrigeringen ACSD-51857 åtgärdar ett problem där långsamt kroniskt jobb utförs `aggregate_sales_report_bestsellers_data` påverkar stor `sales_order` och `sales_order_item` databastabeller. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 är installerat. Korrigerings-ID är ACSD-51857. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kronjobbsprestanda `aggregate_sales_report_bestsellers_data` är långsam på `sales_order` och `sales_order_item` databastabeller.

För att lösa detta har huvuddatafrågan som hämtar data för rapporten skrivits om till ett mer effektivt format. Nu används en underfråga för att fastställa datadelmängden.

För att underfrågan ska fungera så snabbt som möjligt har ett nytt index lagts till för `sales_order` databastabell `SALES_ORDER_STORE_STATE_CREATED` baserat på `store_id`, `state`och `created_at` kolumner.

<u>Förutsättningar</u>

Säkerställ ett stort antal order varje dag.

<u>Steg som ska återskapas</u>

1. Kör `aggregate_sales_report_bestsellers_data` cron-jobb.
1. Kontrollera de data som ska visas på Admin Dashboard under **[!UICONTROL Bestsellers]** -fliken.

<u>Förväntade resultat</u>:

*[!UICONTROL Quantity per source]* under **[!UICONTROL Configuration]** -fliken får inte vara tom.

<u>Faktiska resultat</u>:

*[!UICONTROL Quantity per source]* under **[!UICONTROL Configuration]** är tom.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
