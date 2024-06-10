---
title: '[!DNL UPS] migrering av leveransmetodintegration från [!DNL SOAP] till [!DNL RESTful API]'
promoted: true
description: Tillämpa en patch för att hantera [!DNL UPS] migrering av leveransmetodintegration från [!DNL SOAP] till [!DNL RESTful API] för Adobe Commerce 2.4.4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL UPS] migrering av leveransmetodintegration från [!DNL SOAP] till [!DNL RESTful API]

>[!NOTE]
>
>Om du överförde någon av de tre patcharna från den här artikeln innan **6 juni 2024**: Om du stöter på det här problemet på grund av [!DNL Metric System/SI] mått (kilo och centimeter) som inte används bör du återanvända en av dessa nya, uppdaterade korrigeringsfiler som nu publiceras i den här artikeln för din version av Adobe Commerce/Magento Open Source 2.4.4+/2.4.5+/2.4.6+ en gång till, eftersom du annars inte kan välja [!DNL Metric System/SI] mått på **kilo** och **centimeter** i [!DNL UPS] leveransmetoder i **[!DNL Admin configuration]**. Dessa nya patchar är kompatibla med de tidigare släppta patcharna. Problemet kommer att åtgärdas permanent i den kommande version av Adobe Commerce 2.4.7-p1 som planeras för **11 juni 2024**.

>[!NOTE]
>
>Om du överförde någon av de tre patcharna från den här artikeln innan **10 oktober 2023** bör du återanvända en av dessa patchar som nu publicerats i den här artikeln för din version av 2.4.4+/2.4.5+/2.4.6+ av Adobe Commerce/Magento Open Source igen, eftersom du annars inte kan välja och konfigurera specifika [!DNL UPS] leveransmetoder i **[!DNL Admin configuration]** och du måste aktivera alla. Dessa nya patchar är kompatibla med de tidigare släppta patcharna.

I den här artikeln finns en patch som löser problem med [!DNL United Parcel Service (UPS)] migrering av leveransmetodintegration från [!DNL SOAP] till [!DNL RESTful API] för Adobe Commerce 2.4.4 - 2.4.6-pX.

Enligt de senaste uppdateringarna av [!DNL UPS API] Säkerhetsmodell, [!DNL UPS] har implementerat en [!DNL OAuth 2.0] säkerhetsmodell för alla [!DNL APIs] (Mer information finns i [[!DNL UPS] Guide för migrering av nyckel till Developer Portal Access](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)) för att förbättra den övergripande säkerheten för att minska bedrägerier och förbättra [!DNL API] funktioner.

Den här förändringen påverkar vår nuvarande [!DNL UPS] implementering av leveransmetoder i Adobe Commerce och kräver att vi åtgärdar den aktuella implementeringen och migrerar från [!DNL SOAP API] till [!DNL RESTful API] att kunna ge support [!DNL OAuth 2.0] autentiseringsprotokoll.

**Från juni 2024**, kommer inte Adobe Commerce handlare att kunna interagera med våra nuvarande [!DNL UPS] integreringen, så vi lanserar den här snabbkorrigeringen, som gör att handlare med Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ kan migrera till den senaste [!DNL UPS REST APIs].

Problemet kommer att åtgärdas i Adobe Commerce/Magento Open Source version 2.4.7 och korrigeringen kommer också att ingå i version 2.4.7-beta2 i oktober 2023.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur och lokalt, samt Magento Open Source:

* 2.4.4
* 2.4.4-pX
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6-pX

## Orsaker

The [!DNL UPS] släppt en [säkerhetsuppdatering för [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

Om du har EU (andra ursprung kan uppleva samma problem) som Leveransens ursprung kommer detta att orsaka ett fel i [!DNL UPS REST] begäran: &quot;*En leverans kan inte ha KGS/IN, LBS/CM eller OZS/CM som måttenhet.*&quot;

## Lösning

Använd följande bifogade patchar, beroende på vilken version av Adobe Commerce/Magento Open Source du använder:

För att lösa problemet i versionerna 2.4.4+, 2.4.5+ och 2.4.6+ måste du tillämpa motsvarande korrigering på din version av Adobe Commerce/Magento Open Source nedan.

## Lappa

Använd följande bifogade patchar, beroende på vilken version av Adobe Commerce/Magento Open Source du använder:

### För version 2.4.4, 2.4.4-pX:

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### För version 2.4.5, 2.4.5-pX:

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### För version 2.4.6, 2.4.6-pX:

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

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
