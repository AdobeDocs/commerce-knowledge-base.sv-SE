---
title: 'ACSD-51857: Det långsamma kronjobbet för "aggregat_sales_report_bestsellers_data" påverkar prestandan'
description: Använd patchen ACSD-51857 för att åtgärda Adobe Commerce-problemet där långsamma cron-jobb "aggregate_sales_report_bestsellers_data" påverkar stora databastabeller av typen "sales_order" och "sales_order_item".
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857: Det långsamma kronijobbet för `aggregate_sales_report_bestsellers_data` påverkar prestandan

Korrigeringen ACSD-51857 åtgärdar ett problem där det långsamma cron-jobbet `aggregate_sales_report_bestsellers_data` påverkar stora `sales_order` - och `sales_order_item` databastabeller. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 har installerats. Korrigerings-ID är ACSD-51857. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kronjobbsprestandan för `aggregate_sales_report_bestsellers_data` är långsam på databastabeller för `sales_order` och `sales_order_item`.

För att lösa detta har huvuddatafrågan som hämtar data för rapporten skrivits om till ett mer effektivt format. Nu används en underfråga för att fastställa datadelmängden.

För att underfrågan ska fungera så snabbt som möjligt lades ett nytt index till för databastabellen `sales_order`: `SALES_ORDER_STORE_STATE_CREATED` baserat på kolumnerna `store_id`, `state` och `created_at`.

<u>Förutsättningar</u>

Säkerställ ett stort antal order varje dag.

<u>Steg som ska återskapas</u>

1. Kör cron-jobbet `aggregate_sales_report_bestsellers_data`.
1. Kontrollera de data som ska visas på Admin Dashboard på fliken **[!UICONTROL Bestsellers]**.

<u>Förväntade resultat</u>:

*[!UICONTROL Quantity per source]* under fliken **[!UICONTROL Configuration]** får inte vara tom.

<u>Faktiska resultat</u>:

*[!UICONTROL Quantity per source]* under fliken **[!UICONTROL Configuration]** är tom.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
