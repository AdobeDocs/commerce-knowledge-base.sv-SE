---
title: Adobe Commerce 2.3.6, 2.4.1 CAPTCHA in checkout fungerar inte
description: Den här artikeln innehåller en korrigeringsfil för problemet där funktionen CAPTCHA för utcheckning inte fungerar som väntat på sidan Placera order när du använder tredjepartsbetalningsleverantörer som Paypal Express, Payflow Pro eller CyberSource i Adobe Commerce.
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.1 CAPTCHA in checkout fungerar inte

Den här artikeln innehåller en korrigeringsfil för problemet där funktionen CAPTCHA för utcheckning inte fungerar som väntat på sidan Placera order när du använder tredjepartsbetalningsleverantörer som Paypal Express, Payflow Pro eller CyberSource i Adobe Commerce.

Detta kända problem nämns i vår utvecklardokumentation:

<u>För Adobe Commerce 2.3.6</u>:

* [Adobe Commerce 2.3.6 Versionsinformation: Kända fel](https://devdocs.magento.com/guides/v2.3/release-notes/commerce-2-3-6.html#known-issues)
* [Versionsinformation om Magento Open Source 2.3.6: Kända fel](https://devdocs.magento.com/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

<u>För Adobe Commerce 2.4.1</u>:

* [Adobe Commerce 2.4.1 Versionsinformation: Kända fel](https://devdocs.magento.com/guides/v2.4/release-notes/commerce-2-4-1.html#known-issues)
* [Versionsinformation om Magento Open Source 2.4.1: Kända fel](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-1.html#known-issues)

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) 2.3.6 och 2.4.1
* Magento Open Source 2.3.6 och 2.4.1

## Problem

<u>Steg som ska återskapas</u>

1. Ställ in minst en av dessa betalningsmetoder i Commerce: Paypal Express, Payflow Pro eller CyberSource.
1. Gå till **Admin > Stores > Configuration > Customers > Customer Configuration > CAPTCHA** .
   * Ange **Aktivera CAPTCHA på Storefront** = *Ja* .
   * Markera i **Forms** : *Utcheckning/placeringsordning* , *Inloggning* och *Glömt lösenord* .
   * Ange **Visningsläge** = *Efter antal inloggningsförsök* (för att skapa **Antal misslyckade inloggningsförsök** inställning visas).
   * Ange **Antal misslyckade inloggningsförsök** = *0* (så att captcha fungerar hela tiden).
1. Lägg till en produkt i kundvagnen och försök checka ut den.
1. På sidan Betalningsinformation anger du captcha och försöker checka ut med Paypal Express, Payflow Pro eller CyberSource.

<u>Förväntat resultat:</u>

CAPTCHA-funktionen fungerar som förväntat.

<u>Faktiskt resultat:</u>

Felmeddelandet visas: *Ange CAPTCHA-kod och försök igen.*

## Lösning

Använd någon av patcharna nedan beroende på om du använder Adobe Commerce lokalt/Adobe Commerce i molninfrastrukturen/Magento Open Source 2.3.6 eller 2.4.1.

## Patchar

Patcharna är kopplade till den här artikeln och tillgängliga för hämtning i båda `.composer` och `.git` format.

Om du vill hämta en patch bläddrar du nedåt till slutet av artikeln och klickar på filnamnet, eller klickar på någon av följande länkar:

<u>För Adobe Commerce lokalt/Adobe Commerce i molninfrastruktur/Magento Open Source 2.3.6</u> :

* [Composer patch MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git patch MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u>För Adobe Commerce lokalt/Adobe Commerce i molninfrastruktur/Magento Open Source 2.4.1</u> :

* [Composer patch MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git patch MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

Dessa patchar är inte kompatibla med andra versioner och utgåvor av Adobe Commerce eller Magento Open Source.

## Så här sätter du på plåstret

<u>Kompositkorrigering</u>

Se [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår supportkunskapsbas för instruktioner om Composer patch.

<u>Git patch</u>

Se dokumentation för utvecklare [Använda korrigeringsfiler: Anpassade korrigeringsfiler](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches) för Git-korrigeringsanvisningar för Adobe Commerce/Magento Open Source.
