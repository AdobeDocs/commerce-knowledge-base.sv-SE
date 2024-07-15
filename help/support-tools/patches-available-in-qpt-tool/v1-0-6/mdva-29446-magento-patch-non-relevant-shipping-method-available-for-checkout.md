---
title: "MDVA-29446: Icke-relevant leveranssätt för utcheckning"
description: MDVA-29446-patchen löser problemet där en leveransmetod som inte är tillämplig visas i alternativen för utcheckningsmetoden och, om den är markerad, felmeddelandet "*Fraktfirma med en sådan metod inte hittades null, schablonpris*." visas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat. Problemet är schemalagt att åtgärdas i senare versioner av Adobe Commerce.
exl-id: 74de5ec4-1f57-4d63-8fbc-614b23783ee3
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-29446: Ej relevant leveransmetod för utcheckning

Korrigeringen MDVA-29446 löser problemet där en leveransmetod som inte är tillämplig visas i alternativen för leveransmetoden för utcheckning och, om den är markerad, ett felmeddelande *Transportör med en sådan metod som inte hittas null, schablonsats*. visas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat. Problemet är schemalagt att åtgärdas i senare versioner av Adobe Commerce.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce i molninfrastruktur 2.3.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3-2.4.0.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Du har en leveransmetod som inte är tillämplig men som fortfarande visas i alternativen för utcheckningsmetoden och du kan välja den här leveransmetoden som inte är relevant.

<u>Steg som ska återskapas</u>:

1. Installera ren 2.3-utveckling.
1. Aktivera standardfrekvens och ställ in:

   * Leverera till tillämpliga länder = *Specifika länder*
   * Leverera till specifika länder = *Antarktis*
   * Visa metod om inte tillämpligt = *Ja*

1. Inaktivera alla andra leveransmetoder.
1. Gå till frontend och skapa en kund med en adress i USA.
1. Markera ett objekt och klicka på **Lägg till i kundvagnen**.
1. Klicka på kundvagnen och klicka på **Fortsätt till kassan**.

<u>Faktiska resultat</u>:

1. På sidan **Leverans** ser du följande:

   * Platt hastighet visas
   * Schablonbelopp är $0
1. När användaren har klickat på **Nästa** får användaren följande fel:

*&quot;Det gick inte att hitta bäraren med den här metoden: null, flatrate&quot;*

<u>Förväntade resultat</u>:

* Priset för leveransmetoden är inte synligt om leveransmetoden inte är tillämplig.
* Knappen **Nästa** ska inte vara aktiv.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
