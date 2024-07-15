---
title: 'MDVA-29787: relaterade produkter visas inte'
description: MDVA-29787-korrigeringen åtgärdar ett problem där **Relaterade produkter** inte visas på en Adobe Commerce-butik. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat. Korrigerings-ID är MDVA-29787.
exl-id: ee060d7b-3b0e-4bd5-84e6-fbd6d2fa532f
feature: Cache, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# MDVA-29787: relaterade produkter visas inte

MDVA-29787-korrigeringen löser problemet där **Relaterade produkter** inte visas på en Adobe Commerce-butik. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat. Korrigerings-ID är MDVA-29787.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce om molninfrastruktur 2.3.3.

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.0.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Målregeln för **relaterade produkter** fungerar inte när *är ett av*-villkor används för **Produkter att visa** i Commerce Admin.

>[!NOTE]
>
>Obs! Den här korrigeringen åtgärdar inte befintliga målregler. Du måste återskapa befintliga målregler.

<u>Steg som ska återskapas</u>:

1. Skapa **nytt attribut** (Exempel: test\_Attr).
   * Ange **katalogindatatyp för butiksägare** = *Text.*
   * Ange **Använd för kampanjregelvillkor** = *Ja* i **Egenskaper för Storefront**.
1. Skapa **ny attributuppsättning** (Exempel: test\_set).
1. Lägg till det **nya attributet** i den **nya attributuppsättningen** (Exempel: Lägg till attributet &quot;Test\_Attr&quot; i attributuppsättningen &quot;Test\_Set&quot;).
1. Skapa tre produkter. De är till exempel inställda så här:
   * Produkt1, Test\_Attr = MAGT2NA\_Test3
   * Produkt2, Test\_Attr = 24 MB02
   * Product3, Test\_Attr = 701644329389M
1. Skapa mål **Regel** (**Marknadsföring**)   > **Relaterade produktregler** och klicka på knappen **Lägg till regel** .) med inställningar:
   * **Gäller för** = *Relaterade produkter*
   * **Produkter som ska matchas**
   * Ange det nya attribut du skapade **i** **Steg 1 ovan** som Product1-attributet (Exempel: Test\_Attr = MAGT2NA\_Test3).
   * **Produkter som ska visas** = attributen för de två andra produkterna (Exempel: attributen 24-MB02 och 701644329389M).
1. Spara **regeln**.
1. Kör en omindexering om det behövs.
1. Rensa cache.
1. Öppna Product1 i förgrunden.

<u>Förväntade resultat</u>:

De relaterade produkterna finns.

<u>Faktiska resultat</u>:

De relaterade produkterna saknas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
