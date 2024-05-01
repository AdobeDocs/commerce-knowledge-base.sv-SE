---
title: 'ACSD-50815: Decimalkvantitet för enkel produkt kan inte användas för nytt produktalternativ för paketerad produkt'
description: Använd patchen ACSD-50815 för att åtgärda problemet med Adobe Commerce där decimalkvantiteten för en enkel produkt inte kan användas för ett nytt produktalternativ.
feature: Products
role: Admin
exl-id: f4aa417c-b0eb-4a68-bf1e-fd86770cc72d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-50815: Decimalkvantitet för enkel produkt kan inte användas för nya paketerade produkter

Korrigeringen ACSD-50815 åtgärdar ett problem där decimalkvantiteten för en enkel produkt inte kan användas för ett nytt produktalternativ. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 är installerat. Korrigerings-ID är ACSD-50815. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Decimalkvantiteten för en enkel produkt kan inte användas för ett nytt produktalternativ som paketeras.

<u>Steg som ska återskapas</u>:

1. Logga in som administratör.
1. Skapa en ny enkel produkt.
   * I **[!UICONTROL Advanced Inventory]** fönster, ange [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes].
   * Spara den enkla produkten.
1. Skapa en ny paketerad produkt.
1. Lägg till valfritt alternativ.
1. Lägg till den enkla produkten i det här alternativet.
1. Ange en decimalkvantitet för den enkla produkten i produktalternativet för paketerade produkter. Exempel: 1.5.

<u>Förväntade resultat</u>:

Det går att ange decimalkvantitet. Inga fel visas.

<u>Faktiska resultat</u>:

Felet *Ange ett giltigt nummer i fältet* visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
