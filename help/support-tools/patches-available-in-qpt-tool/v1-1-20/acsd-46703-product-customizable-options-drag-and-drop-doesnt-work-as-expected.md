---
title: 'ACSD-46703: Dra och släpp för produktanpassning fungerar inte'
description: Den här artikeln innehåller en lösning på problemet där dra och släpp för de anpassningsbara alternativen inte fungerar som förväntat.
exl-id: 49b29495-d225-4f34-ac76-b7294a86aea6
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-46703: Dra och släpp för produktanpassning fungerar inte

Korrigeringen ACSD-46703 åtgärdar ett problem där de anpassningsbara alternativen (dra och släpp) inte fungerar som förväntat. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 är installerat. Korrigerings-ID är ACSD-46703. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5

>[!NOTE]
>
>Korrigeringen kan komma att gälla för andra versioner med nya [kvalitetskorrigeringsverktyg]. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användarna kan inte dra och släppa de anpassningsbara alternativen från en sida till en annan.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Lägg till anpassningsbara alternativ till den enkla produkten och se till att du lägger till över 20 alternativ, vilket resulterar i sidnumrering.
1. Försök att flytta ett anpassningsbart alternativ (dra och släpp) inom samma sida.
1. Nu kan du försöka flytta ett anpassningsbart alternativ från sida två till sida ett.

<u>Förväntade resultat</u>:

* Du kan dra och släppa de anpassningsbara alternativen från en sida till en annan.
* Du kan sortera värdena med dra och släpp-funktionen, även för flera sidor.

<u>Faktiska resultat</u>:

Du kan inte flytta något värde till en annan sida med dra och släpp-funktionen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt för Adobe Commerce eller Magento Open Source: [Verktyg för kvalitetspatchar > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden för kvalitetspatchar.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i guiden för verktyget för kvalitetspatchar.
