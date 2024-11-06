---
title: Leveransen kan inte sparas som en URL-nyckel
description: I den här artikeln finns en lösning på problemet när du inte kan spara frakten som en URL-nyckel (_t.ex. /shipping_) för produkter eller CMS-sidor. När du försöker spara URL-nyckeln visas ett fel som anger att URL-nyckeln är en dubblett av en URL.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Det går inte att spara _leverans_ som en URL-nyckel

I den här artikeln finns en lösning på problemet när du inte kan spara frakten som en URL-nyckel (_t.ex. /shipping_) för produkter eller CMS-sidor. När du försöker spara URL-nyckeln visas ett fel som anger att URL-nyckeln är en dubblett-URL.

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.4.x

## Problem

Du kan inte spara en CMS-sida med termen _shipping_ i URL-nyckeln.

<u>Steg som ska återskapas</u>:

Skapa en **[!UICONTROL CMS page]** med URL-nyckeln som _leverans_.

<u>Förväntat resultat</u>:

Sidan sparas med _shipping_ som URL-nyckel.

<u>Faktiskt resultat</u>:

Du kan inte spara eftersom följande fel inträffar:
*Värdet som anges i fältet URL-nyckel skulle generera en URL som redan finns.*

## Orsak

Leverans är ett reserverat ord som definieras i `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## Lösning

Du kan inte använda termen _shipping_ i URL-nyckeln - men du kan använda termen _shipping_ kombinerat med en annan bokstav eller siffra (_T.ex. shipping1 och shipping_).

Även om termen inte behöver vara _shipping_+&lt;ett annat tal eller en annan bokstav>, kan termen vara vilken sträng som helst så länge längden inte överstiger *255* tecken.

## Utför följande steg:

1. Logga in på Adobe Commerce Admin.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Klicka på **[!UICONTROL Add URL Rewrite]**.
1. Välj **[!UICONTROL Custom]** i listrutan **[!UICONTROL Create URL Rewrite]**.
   1. Ange [!UICONTROL Request Path] som **_leverans_**.
   1. I **[!UICONTROL Target Path]** skriver du den nya URL-nyckeln (_Till exempel &quot;shipping1&quot;_).
   1. Välj **[!UICONTROL No]** i listrutan **[!UICONTROL Redirect]**.


      (**Obs!**: Sökvägen för begäran är den som användaren anger i webbläsaren och målsökvägen är den plats där den ska dirigeras om.)

Undvik dessutom att använda dessa nyckelord som är märkta som *reserverade* nyckelord, vilket gör att samma undantag visas. Om du använder något av nyckelorden som listas nedan som ett URL-nyckelvärde visas samma fel.


```
"admin"
"adminAnalytics"
"analytics"
"api"
"backup"
"bulk"
"captcha"
"catalog"
"catalogsearch"
"checkout"
"cms"
"contact"
"cookie"
"customer"
"directory"
"downloadable"
"giftmessage"
"groupedProduct"
"indexer"
"instantpurchase"
"loginascustomer"
"marketplace"
"mui"
"multishipping"
"newsletter"
"oauth"
"paypal"
"persistent"
"productalert"
"releaseNotification"
"reports"
"review"
"robots"
"rss"
"sales"
"search"
"security"
"sendfriend"
"shipping"
"stores"
"swagger"
"swatches"
"tax"
"theme"
"translation"
"vault"
"wishlist"
```

## Relaterad läsning

* [URL-omskrivning](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite) i vår användarhandbok för marknadsföring och marknadsföring.
* [SEO Best Practices](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview) i vår användarhandbok för marknadsföring och marknadsföring.
