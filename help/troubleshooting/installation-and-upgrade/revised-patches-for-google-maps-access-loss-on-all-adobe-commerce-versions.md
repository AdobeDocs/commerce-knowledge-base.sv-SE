---
title: Uppdaterade korrigeringsfiler för åtkomst till Google Maps för alla Adobe Commerce-versioner
description: '"Den här artikeln innehåller en korrigering för Adobe Commerce-handlare som inte är kompatibla med någon av de senaste [!DNL Google Maps] versioner från 3.54+.'''
feature: Install, Upgrade
role: Developer
source-git-commit: 49bc0b643c10c6597d6a905935c36251e92b18f9
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Uppdaterade patchar för [!DNL Google Maps] förlust av åtkomst för alla Adobe Commerce-versioner

I den här artikeln finns en korrigering för Adobe Commerce-handlare som inte är kompatibla med någon av de senaste [!DNL Google Maps] versioner från 3.54+. Den här lösningen är att lösa problemet där Adobe Commerce handlare inte har tillgång till [!DNL Google Maps] i någon version av Adobe Commerce längre.

## Berörda versioner och produkter

* Versioner av Adobe Commerce och/eller annan teknik som används.
* Adobe Commerce *2.4.4* - *2.4.7* på Cloud och On-Premises.

## Problem

På *14 juni 2024* [!DNL Google Maps] version *3,53* har nått slutet av livscykeln och har stängts av av av av [!DNL Google].

Mer information finns i [[!DNL Google Maps] Plattform: Maps JavaScript API] (https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

Adobe Commerce var inte kompatibelt med någon av de senaste [!DNL  Google Maps] versioner från 3.54+.

Inkompatibiliteten orsakades av äldre `prototype.js script`som lästes in genom `lib/web/legacy-build.min.js` åsidosätter funktionen native Array.from, vilket leder till en direkt konflikt med [!DNL  Google Maps] API.

Se [[!DNL Google Maps: JS Best Practices]] (https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Steg som ska återskapas</u> :

1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Pages]** > och klicka på en **[!UICONTROL New Page]**.
1. Expandera innehållsblocket och klicka på redigeringen **[!DNL PageBuilder]** -knappen.
1. Dra kartinnehållsblocket från **[!DNL PageBuilder]** meny till sida.

<u>Förväntat resultat:</u>

[!DNL Google Maps] ska fungera som förväntat.

<u> Faktiskt resultat:</u>

När du släpper kartinnehållsblocket från **[!DNL PageBuilder]** meny till sidan, ett felmeddelande som *&quot;Förlåt! Något gick fel&quot;* visas.

## Lösning

* Alla handlare i någon patchversion av version 2.4.4, 2.4.5, 2.4.6 eller 2.2.7 bör tillämpa dessa patchar på sin version.

## Lappa

Använd följande bifogade patchar, beroende på vilken version av Adobe Commerce det är:

**För version 2.4.4:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_Composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**För version 2.4.5:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_Composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**För version 2.4.6:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_Composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**För version 2.4.7:**
[ACSD-60245_Google_maps_API_2.4.7_Composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**Obs!**

Problemet kommer att åtgärdas permanent i säkerhetspatchen från augusti: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Relaterad läsning

[Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)