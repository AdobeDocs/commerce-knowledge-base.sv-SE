---
title: 'ACSD-49129: Attributet "Content" returneras inte i API-svar för produktmedia'
description: Använd korrigeringsfilen ACSD-49129 för att åtgärda Adobe Commerce-problemet där attributet *content* (*base64-bildkod*) inte returneras i programmeringsgränssnittssvaren för "rest/V1/products/sku/media".
exl-id: b7022046-3f52-4880-81b8-977ed270773f
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-49129: Attributet &quot;Content&quot; returneras inte i API-svar för produktmedia

Korrigeringen ACSD-49129 åtgärdar ett problem där *innehåll* attribute (*[!UICONTROL base64 image code]*) returneras inte i `rest/V1/products/sku/media` API-svar för produktmedia. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.30 är installerat. Korrigerings-ID är ACSD-49129. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The *innehåll* attribute (*[!UICONTROL base64 image code]*) returneras inte i `rest/V1/products/sku/media` API-svar för produktmedia.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt med en bild.
1. Skicka *GET REST API* begäran till `rest/V1/products/<sku>/media` och `rest/V1/products/<sku>/media/<entryId>`.
1. Kontrollera API-svaren.

<u>Förväntade resultat</u>

The *innehåll* attribut med data är tillgängligt via REST API.

<u>Faktiska resultat</u>

The *innehåll* Attributet finns inte i API-svaren.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
