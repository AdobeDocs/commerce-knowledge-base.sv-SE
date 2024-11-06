---
title: 'MDVA-42283: Formatet Date-time för franska är ogiltigt'
description: Korrigeringen MDVA-42283 åtgärdar ett problem där datumet-time-formatet i administrationsorderrutnätet för franska är ogiltigt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-42283. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 9b470e7b-4b73-4100-9a9d-1a45a5ac628b
feature: CMS
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42283: Formatet Date-time för franska är ogiltigt

Korrigeringen MDVA-42283 åtgärdar ett problem där datumet-time-formatet i administrationsorderrutnätet för franska är ogiltigt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-42283. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Formatet för datum/tid i administrationsorderrutnätet för franska är ogiltigt.

<u>Steg som ska återskapas</u>:

1. Skapa en beställning, kundsida, CMS-sida eller CMS Block.
1. Gå till **Admin** > **Kontoinställningar** och ange gränssnittets nationella inställningar för admin till **Français (Kanada)**/**français (Kanada)(fr_CA)** eller **Brasiliansk portugisiska (pt_BR)**.
1. Observera värdet i datumkolumnen för rutnät för beställningar, utleverans, kreditnota, kunder, CMS-sidor eller CMS-block.

<u>Förväntade resultat</u>:

Datumet har det format som visas på den faktiska redigeringssidan för entiteten.

<u>Faktiska resultat</u>:

Datum-tid-värdet är felaktigt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
