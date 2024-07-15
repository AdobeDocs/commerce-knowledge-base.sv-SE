---
title: '[!DNL USPS] Stöd för snabbkorrigering för leveransmetod för markförmåner för AC-9182'
promoted: true
description: Använd en patch för att hantera problemet med  [!DNL USPS] markförmåner, leveransmetod AC-9182 för Adobe Commerce 2.4.4 - 2.4.6-p2.
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] Stöd för snabbkorrigering för leveransmetod för markförmåner för AC-9182

I den här artikeln finns en patch som löser problemet AC-9182 för den nya leveransmetoden **[!DNL USPS]Ground Advantage** i Adobe Commerce 2.4.4 - 2.4.6-p2.

Den 9 juli 2023 släppte United States Postal Service ([!DNL USPS]) en ny leveransmetod, [[!DNL USPS] Ground Advantage](https://www.usps.com/ship/ground-advantage.htm).

Den nya leveransmetoden ersätter de tre viktigaste leveranssätten:

* [!DNL USPS] butiksområde
* Pakettjänsten [!DNL USPS] i första klass
* [!DNL USPS] Markering av paket

[[!DNL USPS] meddelade](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works) att från och med den 30 september 2023 kommer dessa tre leveransmetoder att upphöra och alla kunder måste använda den nya metoden **[!DNL USPS]Ground Advantage** i stället.

Efter den 30 september 2023 kommer alla Adobe Commerce-handlare som använder leveransmetoden USPS inte att kunna få frakt från [!DNL USPS] genom att använda dessa tre äldre leveransmetoder längre.

Detta problem kommer att åtgärdas i de kommande säkerhetsutgåvorna i oktober 2023, i version 2.4.6-p3, 2.4.5-p5 och 2.4.4-p6.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur och lokalt, samt Magento Open Source:

* 2.4.4
* 2.4.4-p1
* 2.4.4-p2
* 2.4.4-p3
* 2.4.4-p4
* 2.4.4-p5
* 2.4.5
* 2.4.5-p1
* 2.4.5-p2
* 2.4.5-p3
* 2.4.5-p4
* 2.4.6
* 2.4.6-p1
* 2.4.6-p2

## Orsak

[!DNL USPS] har gjort en [!DNL API]-uppdatering.

## Lösning

För att lösa problemet i versionerna 2.4.4, 2.4.5 och 2.4.6 måste du installera AC-9182-korrigeringen nedan.

## Lappa

Korrigeringen är kopplad till den här artikeln. Klicka på följande länk om du vill hämta den:

[AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## Så här sätter du på plåstret

Zippa upp filen och se [Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) i vår kunskapsbas för support för instruktioner.

## Hur man vet om plåstren har använts

Eftersom det inte är enkelt att kontrollera om problemet har åtgärdats kanske du vill kontrollera om korrigeringsfilen för AC-9182 har installerats korrekt.

<u>Du kan göra detta genom att utföra följande steg</u>:

1. [Installera  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Kör kommandot:

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. Du bör se utdata som liknar detta, där AC-9182 returnerar statusen *Används*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
