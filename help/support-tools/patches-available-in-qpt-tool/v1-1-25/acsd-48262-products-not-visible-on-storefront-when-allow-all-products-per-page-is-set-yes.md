---
title: 'ACSD-48262: produkter som inte är synliga i butiken när [!UICONTROL Allow All Products Per Page] är inställt [!UICONTROL Yes]'
description: Använd korrigeringsfilen ACSD-48262 för att åtgärda Adobe Commerce-problemet där produkterna inte syns i butiken när [!UICONTROL Allow All Products Per Page] inställningen är inställd på [!UICONTROL Yes].
exl-id: 327cad03-441d-4adb-8a10-802f06d3fcd1
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-48262: produkter som inte visas i butiken när [!UICONTROL Allow All Products Per Page] är inställt *[!UICONTROL Yes]*

Korrigeringen ACSD-48262 åtgärdar ett problem där produkter inte syns i butiken när [!UICONTROL Allow All Products Per Page] inställningen är inställd på *[!UICONTROL Yes]*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 är installerat. Korrigerings-ID är ACSD-48262. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Korrigeringen ACSD-48262 åtgärdar ett problem där produkter inte syns i butiken när [!UICONTROL Allow All Products Per Page] inställningen är inställd på *[!UICONTROL Yes]*.

<u>Steg som ska återskapas</u>:

1. Skapa en testkategori.
1. Skapa en testprodukt i testkategorin.
1. Bläddra i produkten för att testa kategorisidan i butiken och kontrollera att produkten är synlig.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** och ange [!UICONTROL Allow All Products Per Page] ange till *[!UICONTROL Yes]*.
1. Rensa cache.
1. Kontrollera kategorisidan i butiken.

<u>Förväntade resultat</u>:

Produkten syns.

<u>Faktiska resultat</u>:

Produkten syns inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
