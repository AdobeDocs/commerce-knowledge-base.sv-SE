---
title: Migrering av integrering av [!DNL FedEx]-leveransmetod från SOAP till RESTful API
promoted: true
description: Använd en patch för att hantera migrering av  [!DNL FedEx] leveransmetodintegrering från SOAP till RESTful API för Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7a54e992e365238ec7c764225a31cd3b6b8ad019
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Migrering av integrering av [!DNL FedEx]-leveransmetod från SOAP till RESTful API

>[!WARNING]
>
>Använd patchen ACSD-61622 från version [!DNL Quality Patches Tool] (QPT) 1.1.57 i stället för den tidigare patchen. Den nya korrigeringen är kompatibel med Adobe Commerce-versioner (alla distributionsmetoder) 2.4.6-p1 - 2.4.6-p8. Det kan bli tillämpligt på andra versioner med nya [!DNL Quality Patches Tool]-versioner.
>
>Mer information finns i artikeln [ACSD-61622-korrigering](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-61622-fedex-account-specific-rates-missing-from-response) i Adobe Commerce-handboken.

>[!WARNING]
>
>Innan du installerar den nya korrigeringen måste du avinstallera den tidigare korrigeringen som finns i den här artikeln. Instruktioner om hur du avinstallerar korrigeringsfiler finns i [Återställa en anpassad korrigeringsfil](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches#revert-a-custom-patch) i användarhandboken.


I den här artikeln finns en patch som löser problem med migrering av [!DNL FedEx]-leveransmetodintegration från SOAP till RESTful API för Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

Spårning av [!DNL FedEx Web Services], adressvalidering och validering av WSDLS (Postal Codes Web Services Definition Languages) upphörde 15 maj 2024. Den SOAP baserade [!DNL FedEx Web Services] är i utvecklingsbegränsning och har ersatts med [!DNL FedEx] RESTFUL-API:er. Mer information finns i [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Den här ändringen påverkar vår nuvarande implementering av [!DNL FedEx]-leveransmetoder i Adobe Commerce och kräver att vi korrigerar vår nuvarande implementering och migrerar från inaktuella SOAP-API:er till de senaste [!DNL FedEx] RESTFUL-API:erna.

Från och med 15 maj 2024 kommer Adobe Commerce-kunder inte att kunna använda vår nuvarande [!DNL FedEx]-integration med leveransmetoden, så Adobe släpper den här snabbkorrigeringen som gör att Adobe Commerce 2.4.4+-kunder kan använda de senaste [!DNL FedEx] RESTFUL-API:erna istället för de borttagna SOAP.


## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur och lokalt, samt Magento Open Source:

* 2.4.4-p4
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6-pX

## Orsak

[!DNL FedEx] har ersatt sina SOAP-baserade API:er och ersatt dem med RESTful i stället. Se [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

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

Zippa upp filen och se [Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=sv-SE) i vår kunskapsbas för support för instruktioner.

## Hur man vet om plåstren har använts

Eftersom det inte är enkelt att kontrollera om problemet har åtgärdats kanske du vill kontrollera om korrigeringen har installerats korrekt. Detta använder (exempel: *AC-9363*) som den korrigering som ska kontrolleras.

<u>Du kan göra detta genom att utföra följande steg</u>:

1. [Installera  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE).
1. Kör kommandot:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Du bör se utdata som liknar detta, där AC-9363 returnerar statusen *Används*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
