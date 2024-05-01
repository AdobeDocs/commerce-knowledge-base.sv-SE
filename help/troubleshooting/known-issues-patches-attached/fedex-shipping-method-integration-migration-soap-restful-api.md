---
title: '[!DNL FedEx] migrering av leveransmetodintegration från SOAP till RESTful API'
promoted: true
description: Tillämpa en patch för att hantera [!DNL FedEx] migrering av leveransmetodintegration från SOAP till RESTful API för Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# [!DNL FedEx] migrering av leveransmetodintegration från SOAP till RESTful API

I den här artikeln finns en patch som löser problem med [!DNL FedEx] migrering av leveransmetodintegration från SOAP till RESTful API för Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

[!DNL FedEx Web Services] spårning, adressvalidering och validering av WSDLS (Postal Codes Web Services Definition Languages) kommer att upphöra den 15 maj 2024. SOAP-baserad [!DNL FedEx Web Services] är i utvecklingsbegränsning och har ersatts med [!DNL FedEx] RESTFUL-API:er. Mer information finns i [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Den här förändringen påverkar vår nuvarande [!DNL FedEx] implementering av leveransmetoder i Adobe Commerce och kräver att vi åtgärdar den aktuella implementeringen och migrerar från inaktuella SOAP API:er till den senaste [!DNL FedEx] RESTFUL-API:er.

Från och med 15 maj 2024 kommer Adobe Commerce-kunder inte att kunna använda våra nuvarande [!DNL FedEx] integrering av fraktmetoder, så Adobe släpper denna programfix som gör att kunder med Adobe Commerce 2.4.4+ kan använda den senaste [!DNL FedEx] RESTFUL-API:er i stället för de inaktuella SOAP-API:erna.


## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur och lokalt, samt Magento Open Source:

* 2.4.4-p4
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6-pX

## Orsak

The [!DNL FedEx] ersätter sina SOAP-baserade API:er och ersätter dem med RESTful i stället. Se [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

## Lösning

Använd följande bifogade patchar, beroende på vilken version av Adobe Commerce/Magento Open Source du använder:

För att lösa problemet i versionerna 2.4.4+, 2.4.5+ och 2.4.6+ måste du tillämpa motsvarande korrigering på din version av Adobe Commerce/Magento Open Source nedan.

## Lappa

Använd följande bifogade patchar, beroende på vilken version av Adobe Commerce/Magento Open Source du använder:

### För version 2.4.4-p4:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### För version 2.4.5, 2.4.5-pX:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### För version 2.4.6, 2.4.6-pX:


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


## Så här sätter du på plåstret

Zippa upp filen och se [Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) i vår kunskapsbas för support för instruktioner.

## Hur man vet om plåstren har använts

Eftersom det inte är enkelt att kontrollera om problemet har åtgärdats kanske du vill kontrollera om korrigeringen har installerats korrekt. Detta använder (exempel: *AC-9363*) som den korrigering som ska kontrolleras.

<u>Du kan göra detta genom att utföra följande steg:</u>:

1. [Installera [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Kör kommandot:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Du bör se utdata som liknar detta, där AC-9363 returnerar *Används* status:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
