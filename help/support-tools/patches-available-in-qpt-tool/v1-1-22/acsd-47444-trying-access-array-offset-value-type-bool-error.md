---
title: '"ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_ fel vid åtkomst till vissa kategorisökvägar för kända produkter i PHP 7.4'
description: Använd patchen ACSD-47444 för att åtgärda Adobe Commerce-problemet där det finns en[!UICONTROL Trying to access array offset on value of type bool]_ fel vid åtkomst till vissa kategorisökvägar för kända produkter, i PHP 7.4.
exl-id: dfe803d0-bcff-40e6-a759-8c2243235ea8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-4744: _[!UICONTROL Trying to access array offset on value of type bool]_fel vid åtkomst till vissa kategorisökvägar som inte finns för kända produkter i PHP 7.4

ACSD-47444- plåstret löser problemet där du ser _[!UICONTROL Trying to access array offset on value of type bool]_fel vid åtkomst till vissa kategorisökvägar för kända produkter i PHP 7.4. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 är installerat.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Följande fel inträffar: _[!UICONTROL Trying to access array offset on value of type bool]_PHP 7.4, när man använder vissa icke-befintliga kategorisökvägar för kända produkter.

<u>Förutsättningar</u>:

PHP 7.4.

<u>Steg som ska återskapas</u>:

1. Skapa en ny produkt - med namnet&quot;test&quot;.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > uppsättning **[!UICONTROL Generate "category/product" URL Rewrites]** = _Nej_.
1. Gå till butiken och gå till URL:en som ../abc/test.html (&quot;abc&quot; - should not exist).

<u>Förväntade resultat</u>:

404 sidor.

<u>Faktiska resultat</u>:

500-fel:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
