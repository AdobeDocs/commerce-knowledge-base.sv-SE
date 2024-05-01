---
title: "ACSD-54680: B2B-offert för en produkt med flera tilldelade källor kan inte bearbetas"
description: Använd patchen ACSD-54680 för att åtgärda Adobe Commerce-problemet där B2B-offerten för en produkt med flera tilldelade källor inte kan bearbetas.
feature: B2B
role: Admin, Developer
exl-id: 4d05714c-d32d-46f3-b857-81704c9e96cd
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-54680: B2B-offert för en produkt med flera tilldelade källor kan inte behandlas.

Korrigeringen ACSD-54680 åtgärdar ett problem där B2B-offerten för en produkt med flera tilldelade källor inte kan bearbetas. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.40 är installerat. Korrigerings-ID är ACSD-54680. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

B2B-offert för en produkt med flera tilldelade källor kan inte bearbetas.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** och skapa två nya källor: **Källa 1** och **Källa 2**.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** och skapa en ny Stock: **Stock A**, tilldela den till huvudwebbplatsen och tilldela **Källa 1** och **Källa 2** till den.
1. Skapa en enkel produkt, tilldela **Källa 1** och **Källa 2**, och ange Antal = *2* för varje källa. (produktens säljbara kvantitet bör vara *4* som ett resultat).
1. Skapa ett företag.
1. Gå till **[!UICONTROL Storefront]** och logga in på företagskontot.
1. Lägg den enkla produkten i kundvagnen med kvantitet = *4*.
1. Öppna *[!UICONTROL Shopping cart]* och klicka **[!UICONTROL Request a quote]** -knappen.
1. Lägg till en kommentar och ett citattecken och klicka på **[!UICONTROL Send a Request]** -knappen.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Öppna nyligen skickad offert.

<u>Förväntade resultat</u>:

De angivna artiklarna innehåller den beställda produkten.

<u>Faktiska resultat</u>:

Sidavsnittet med citattecken är tomt och det går inte att bearbeta citattecknet.
`var/log/system.log` innehåller

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
