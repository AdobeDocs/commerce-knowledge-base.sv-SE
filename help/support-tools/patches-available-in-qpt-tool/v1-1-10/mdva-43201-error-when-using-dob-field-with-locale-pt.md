---
title: 'MDVA-43201: Error when using DOB field with locale PT'
description: MDVA-43201-korrigeringen löser problemet där ett fel inträffar när DOB-kundattributet används i kundregistreringsformuläret för den portugisiska språkinställningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Korrigerings-ID är MDVA-43201. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201: Fel vid användning av DOB-fält med nationella inställningar för PT

MDVA-43201-korrigeringen löser problemet där ett fel inträffar när DOB-kundattributet används i kundregistreringsformuläret för den portugisiska språkinställningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Korrigerings-ID är MDVA-43201. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När DOB-kundattribut läggs till i kundregistreringsformuläret för portugisiska, ger formuläret felet *Argument 1 som skickas till iterator_to_array() att implementera gränssnitt som kan skickas, null angivet*.

<u>Förutsättningar</u>:

B2B-moduler är installerade.

<u>Steg som ska återskapas</u>:

1. Gå till Admin > **Butiker** > **Konfiguration** > **Allmänt** > **Språkalternativ**, ange Språk till **Portugisiska (Portugal)** och klicka på **Spara**.
1. Indexera om och rensa cache.
1. Gå till **Store** > **Attribut** > **Kund**.
1. Öppna DOB-kundattributet och ange **Visa på Storefront** till **Ja**.
1. Välj alla från **Formulär att använda i**.
1. Spara attributet.
1. Gå till sidan Skapa nytt konto i förgrunden.

<u>Förväntade resultat</u>:

Kundregistreringsformuläret för den portugisiska butiken ger inget fel när DOB-attributet läggs till.

<u>Faktiska resultat</u>:

Kundregistreringsformuläret för den portugisiska butiken returnerar ett fel när DOB-attributet läggs till.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
