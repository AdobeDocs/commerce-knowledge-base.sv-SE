---
title: 'ACSD-51265: Optimera omindexering för paketerade produkter'
description: Använd patchen ACSD-51265 för att åtgärda Adobe Commerce-problemet där omindexeringsprestandan "catalog_product_price" är låg när det finns för många paketerade produkter i systemet.
feature: Products, Price Indexer
role: Admin
exl-id: ddf23c19-b1ed-4064-adbc-58707eb63cc9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-51265: Optimera omindexering för paketerade produkter

Korrigeringen ACSD-51265 åtgärdar ett problem där `catalog_product_price` omindexeringsprestanda är låg när det finns för många paketerade produkter i systemet. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 är installerat. Korrigerings-ID är ACSD-51265. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Katalogproduktprisens omindexeringsprestanda är låg när det finns för många paketerade produkter i systemet.

<u>Steg som ska återskapas</u>:

1. Generera en katalog med minst *10 000* paketerade produkter med dynamiska prisalternativ.
1. Kör omindexering av produktpris.

<u>Förväntade resultat</u>

Det tar mindre än 15 minuter att omindexera produktpriset.

<u>Faktiska resultat</u>

Det tar mer än en timme att omindexera produktpriset.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
