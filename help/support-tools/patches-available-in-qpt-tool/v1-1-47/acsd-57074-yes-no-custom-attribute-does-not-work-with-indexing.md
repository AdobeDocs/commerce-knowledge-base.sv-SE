---
title: '"ACSD-57074: *Jet/Nej*-attributet med prefixet "price_*" i attributet "attribute_code" fungerar inte med indexering"'
description: Använd patchen ACSD-57074 för att åtgärda Adobe Commerce-problemet där det anpassade attributet *Yes/No* med prefixet "price_*" i attributet "attribute_code" inte fungerar med indexering.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: c620722f-a66d-4cae-9614-becec589a78c
source-git-commit: 4197f2a8f3d4775d3459b17bd92fa51a54ff9607
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-57074: *Ja/Nej* anpassat attribut med `price_*` prefix in `attribute_code` attribut fungerar inte med indexering

Korrigeringen ACSD-57074 åtgärdar ett problem där *Ja/Nej* anpassat attribut med `price_*` i `attribute_code` fungerar inte med indexering. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.47 är installerat. Patch-ID:t är ACSD-57074. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The *Ja/Nej* anpassat attribut med `price_*` i `attribute_code` fungerar inte med indexering.

<u>Steg som ska återskapas</u>:

1. Skapa ett anpassat produktattribut med följande alternativ:
   * *[!UICONTROL Catalog Input Type]*: *Ja/Nej*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Ja*
1. Tilldela attributet till standardattributuppsättningen.
1. Skapa en produkt med det attribut vi skapade.
1. Tilldela den produkt vi nyss skapade till en kategori.
1. Kör fullständig omindexering.

<u>Förväntade resultat</u>:

Produkten visas i den tilldelade kategorin.

<u>Faktiska resultat</u>:

Produkten visas inte på framsidan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
