---
title: 'MDVA-38929: Fakturan med FPT visar fel summa'
description: MDVA-38929-korrigeringen löser problemet där fakturan med FPT visar en felaktig totalsumma när ordern betalas med butikskrediter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-38929. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 1ed0e311-f4a5-4dc0-98fc-fc1cc9458516
feature: Invoices, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-38929: Fakturan med FPT visar fel summa

MDVA-38929-korrigeringen löser problemet där fakturan med FPT visar en felaktig totalsumma när ordern betalas med butikskrediter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 har installerats. Korrigerings-ID är MDVA-38929. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Fakturan med FPT visar en felaktig totalsumma när ordern betalas med butikskrediter.

<u>Steg som ska återskapas</u>:

1. Skapa en kund och se till att kunden har butikskrediter som täcker ordern.
1. Aktivera FPT och lägg till FPT i en produkt.
1. Logga in direkt när kunden just har skapat.
1. Lägg produkten med FPT i kundvagnen.
1. Checka ut och betala med butikskrediter. Det ska vara en nolllöneorder.
1. Gå till Beställningar och fakturera ordern manuellt.
1. Kontrollera totalsumman för fakturan.

<u>Förväntade resultat</u>:

* Fakturans totalsumma är noll.
* Det totala betalda orderbeloppet är noll.

<u>Faktiska resultat</u>:

* Fakturans totalsumma visar fortfarande FPT-beloppet.
* Det totala betalda beloppet visar fortfarande beloppet för bildrutorna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
