---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* anges till Ja utan *[!UICONTROL Use in Search]* option'
description: Använd korrigeringsfilen ACSD-50887 för att åtgärda Adobe Commerce-problemet där produktattributsegenskapen *[!UICONTROL Use in Search Results Layered Navigation]* kan anges till *Ja* utan *[!UICONTROL Use in Search]* alternativet anges också till *Ja*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-5087: *[!UICONTROL Use in Search Results Layered Navigation]* ange till *Ja* utan *[!UICONTROL Use in Search]* option

Korrigeringen ACSD-50887 åtgärdar ett problem där egenskapen för produktattribut åtgärdas *[!UICONTROL Use in Search Results Layered Navigation]* kan anges till *Ja* utan *[!UICONTROL Use in Search]* kan också ställas in på *Ja*. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.36 är installerat. Korrigerings-ID är ACSD-50887. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Egenskapen för produktattribut *[!UICONTROL Use in Search Results Layered Navigation]* kan anges till *Ja* utan *[!UICONTROL Use in Search]* kan också ställas in på *Ja*.

De här inställningarna har utformats för att användas tillsammans. När plåstret appliceras, när *[!UICONTROL Use in Search]* option is set to *Nej*, *[!UICONTROL Use in Search Results Layered Navigation]* alternativet är dolt för att fungera som om det även var inställt på *Nej*.

<u>Steg som ska återskapas</u>:

1. Gå till Admin **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** och skapa ett attribut med flervalstypen och ange följande:

   * *[!UICONTROL Use in Search]= Nej*
   * *[!UICONTROL Use in Layered Navigation]= (Valfritt alternativ)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Ja*
   * *Namn = Test_attribute*
   * *Alternativ*:
      * *Sticker*
      * *Väljare*

1. Lägg till det nya attributet i standardattributuppsättningen.
1. Skapa två produkter:

   1. Första produkten:
      * Namn = Sticker
      * Ange pris, ANTAL, vikt till 1
      * Test_attribute = välj alternativ *Sticker*

   1. Andra produkten:
      * Namn = Väljare
      * Ange pris, ANTAL, vikt till 1
      * Test_attribute = välj båda alternativen

1. Kör `catalogsearch_fulltext` omindexera:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Sök efter ordet *klistermärke* på butiken.

<u>Förväntade resultat</u>:

Bara produkten *Sticker* returneras eftersom [!DNL Elasticsearch] indexerar inte Test_attribute när *[!UICONTROL Use in Search]* har angetts till *Nej*.

<u>Faktiska resultat</u>:

Båda produkterna returneras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
