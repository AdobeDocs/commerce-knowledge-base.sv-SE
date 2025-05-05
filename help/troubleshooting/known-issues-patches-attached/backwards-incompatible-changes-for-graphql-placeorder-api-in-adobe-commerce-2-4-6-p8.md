---
title: "Bakåt inkompatibla ändringar för  [!DNL GraphQL] &grave;placeOrder&grave; [!DNL API] i Adobe Commerce 2.4.6-p8"
promoted: true
description: Den här artikeln innehåller en patch för det kända Adobe Commerce version 2.4.6-p8 Cloud och lokala problemet där placeOrder  [!DNL GraphQL API] inte returnerar ett förväntat felsvar, vilket framgår av tidigare 2.4.6-korrigeringsversioner. Detta kan leda till en trasig utcheckningsupplevelse för handlare som använder PWA storefront eller någon annan  [!DNL GraphQL API]-baserad butik för sina butiker.
feature: Checkout, REST, GraphQL
role: Developer
source-git-commit: 01b79c75df34de20f1ff50ab40c0a8d608ffa779
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Bakåtkompatibla ändringar för [!DNL GraphQL] `placeOrder` [!DNL API] i Adobe Commerce 2.4.6-p8

Den här artikeln innehåller en patch för det kända Adobe Commerce version 2.4.6-p8 Cloud och lokala problemet där `placeOrder` [!DNL GraphQL API] inte returnerar ett förväntat felsvar, vilket framgår av tidigare 2.4.6-korrigeringsversioner. Detta kan leda till en trasig utcheckningsupplevelse för handlare som använder [!DNL PWA] storefront eller någon annan [!DNL GraphQL API]-baserad butik för sina butiker.

>[!NOTE]
>
>Kontakta supporttjänsterna om du råkar ut för problem med att tillämpa korrigeringen.

## Berörda produkter och versioner

* Adobe Commerce i molnet 2.4.6-p8
* Adobe Commerce lokal 2.4.6-p8

## Problem

Efter uppgraderingen av Adobe Commerce 2.4.6-p8-patchen med endast säkerhet returnerar [`placeOrder` [!DNL GraphQL API]](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/) inget förväntat felsvar, vilket framgår av tidigare 2.4.6-korrigeringsversioner. Detta kan leda till en trasig utcheckningsupplevelse för handlare som använder [!DNL PWA] storefront eller någon annan [!DNL GraphQL API]-baserad butik för sina butiker.

<u>Steg för att återskapa</u>:

Kör `placeOrder` [!DNL GraphQL]-begäran där du förväntar dig ett felsvar.

<u>Förväntat resultat</u>:

Du får ett förväntat felsvar.

<u>Faktiskt resultat</u>:

I stället för ett förväntat felsvar får du ett godkänt svar, men med en ny `errors`-nyckel som ser ut så här:

```
{
    "data": {
        "placeOrder": {
            "order": null,
            "__typename": "PlaceOrderOutput"
        }
    }
}
```

## Lösning för Adobe Commerce i molnet och Adobe Commerce On-local Software

Lös problemet genom att applicera plåstret.
Klicka på följande länk om du vill hämta den:

[ac-13283-composer-patch.zip](assets/ac-13283-composer-patch.zip)

## Så här sätter du på plåstret

Zippa upp filen och se [Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=sv-SE) i vår kunskapsbas för support för instruktioner.

## Endast för Adobe Commerce på molnhandlare - Hur du ser om korrigeringsfiler har tillämpats

Eftersom det inte är enkelt att kontrollera om problemet har åtgärdats, kanske du vill kontrollera om korrigeringen har installerats korrekt.

<u>Du kan göra detta genom att utföra följande steg, med exempelfilen `VULN-27015-2.4.7_COMPOSER.patch` **som exempel</u>**:

1. [Installera  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE).
1. Kör kommandot:<br>
   ![ac-13283-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Du bör se utdata som liknar detta, där VULN-27015 returnerar statusen *Används*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

