---
title: 'MDVA-37364: Anpassat kundattribut för datumtyp, brytningsgränssnitt för stödraster'
description: MDVA-37364-korrigeringen löser problemet där det anpassade kundattributet av datumtyp bryter användargränssnittet för kundstödraster. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Patch-ID:t är MDVA-37364. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.4.
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364: Anpassat kundattribut för datumtyp, brytningsgränssnitt för stödraster

MDVA-37364-korrigeringen löser problemet där det anpassade kundattributet av datumtyp bryter användargränssnittet för kundstödraster. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 har installerats. Patch-ID:t är MDVA-37364. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0-2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Anpassat kundattribut av datumtyp bryter användargränssnittet för kundstödraster.

<u>Steg som ska återskapas</u>:

1. Skapa ett anpassat attribut med datumtyp:
   * Gå till **Lagrar** > **Attribut** > **Lägg till attribut**.
   * Ställ in Indatatyp till Datum.
   * Ställ in alternativet Lägg till i kolumn till Ja.
   * Spara attributet.
1. Gå till **Admin** > **Kunder** > **Alla kunder**.
   * Lägg till det nya anpassade attributet i rutnätet från kolumnalternativet.
1. Skapa/redigera en kund och ange värdet för det anpassade datumattributfältet som skapades.
1. Spara, indexera om och rensa cache.
1. Gå till **Kunder** > **Alla kunder**.
   * Kontrollera kundens rutnät.

<u>Förväntade resultat</u>:

Admin Customer Grid visar alla data inklusive det nya anpassade datumattributet utan att kundens gränssnitt bryts.

<u>Faktiska resultat</u>:

Gränssnittet för administratörskundstödraster är brutet.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
