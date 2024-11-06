---
title: 'MDVA-32776: Stock-status har inte uppdaterats med orderplacering'
description: MDVA-32776-korrigeringen åtgärdar ett problem där lagerstatusen inte uppdateras när en order läggs men inte skickas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 är installerat. Patch-ID:t är MDVA-32776. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776: Stock-status har inte uppdaterats med orderplacering

MDVA-32776-korrigeringen åtgärdar ett problem där lagerstatusen inte uppdateras när en order läggs men inte skickas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 har installerats. Patch-ID:t är MDVA-32776. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.0

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerstatusen uppdateras inte när en order placeras men inte skickas.

<u>Förutsättningar</u>:

1. Lagermodulen är installerad.
1. Visa färdiga produkter är inställt på *Ja*.

   Gå till **Lager** > **Konfiguration** > **Katalog** > **Lager** > **Visa ej lagrade produkter** = *Ja* om du vill ange inställningar.

<u>Steg som ska återskapas</u>:

1. Skapa två enkla produkter med kvantitet = 11 och 22.
1. Skapa en grupperad produkt med hjälp av de enkla produkter som skapas i steg 1.
1. Lägg grupperade produkter i varukorgen genom att ange en produktkvantitet till 11 och göra den andra enkla produkten till lagerförd.
1. Slutför utcheckningen och lägg ordern.

<u>Förväntade resultat</u>:

Grupperade produkter visar `out-of-stock` etiketter när associerade enkla produkter lämnar lagret.

<u>Faktiska resultat</u>:

1. Den enkla produkten med kvantitet = 11 har slut på lager.
1. Den grupperade produkten visar inte något *ej i lager*-meddelande för produkten med kvantitet = 11. Om du lägger till den här produkten i kundvagnen uppstår dock ett *fel som inte finns i lager*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
