---
title: 'MDVA-31007: display för anpassade adressattribut'
description: Korrigeringen MDVA-31007 löser problemet där anpassade adressattribut inte visas korrekt på sidan med orderinformation i området Mitt konto och i serverdelen (på platsen **Sales&gt; Orders**). Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007: visa anpassade adressattribut

Korrigeringen MDVA-31007 löser problemet där anpassade adressattribut inte visas korrekt på sidan med orderinformation i området Mitt konto och i serverdelen (på platsen **Försäljning > Beställningar**). Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce om molninfrastruktur 2.4.0

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Logga in på Admin Backend.
1. Navigera till **Butiker** > **Attribut** > **Kundadresser**.
1. Skapa två attribut:

   * Ange indatatyp: *Listruta*.
   * Ange indatatyp: *Text*.

1. Navigera till **Lager** > **Konfigurationer** > **Kund** > **Kundkonfigurationer**.
1. Välj *Omfång* som **standardlagringsvy**.
1. Expandera avsnittet **Adressmall**. Uppdatera *Text*, *Text en rad* och *HTML* om du vill inkludera de två anpassade attributen ovan:

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. Öppna Storefront.
1. Skapa och logga in med en användare.
1. Gå till **Mitt konto** > **Adressbok** och lägg till en ny adress (fyll i de två anpassade attributen).
1. Lägg en produkt i kundvagnen och beställ.
1. Klicka på länken **Ordernummer** på sidan för slutförd beställning.
1. Gå till avsnittet **Beställningsinformation** på sidan med beställningsinformation.
1. Gå till **Backend** > **Försäljning** > **Beställningar**, klicka på ovanstående ordning och observera avsnittet **Adressinformation**.

<u>Förväntade resultat</u>:

På både frontend och backend visas fakturerings- och leveransadressen som förväntat.

<u>Faktiska resultat</u>:

Faktureringsadressen visas inte korrekt på både klientsidan och serverdelen. Det valda alternativet för attributet dropdown saknas, och värdet för indataattributet innehåller attributkoden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
