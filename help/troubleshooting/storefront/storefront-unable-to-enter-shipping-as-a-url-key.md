---
title: Det går inte att spara "leverans" som URL-nyckel
description: I den här artikeln finns en lösning på problemet när du inte kan spara"leverans" som en URL-nyckel (t.ex."/leverans") för produkter eller CMS-sidor. När du försöker spara URL-nyckeln visas ett fel som anger att URL-nyckeln är en dubblett-URL.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Det går inte att spara &quot;leverans&quot; som URL-nyckel

I den här artikeln finns en lösning på problemet när du inte kan spara&quot;leverans&quot; som en URL-nyckel (t.ex.&quot;/leverans&quot;) för produkter eller CMS-sidor. När du försöker spara URL-nyckeln visas ett fel som anger att URL-nyckeln är en dubblett-URL.

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.4.x

## Problem

Du kan inte spara en CMS-sida med termen&quot;leverans&quot; i URL-nyckeln.

<u>Steg som ska återskapas</u>:

Skapa en CMS-sida med URL-nyckeln som&quot;leverans&quot;.

<u>Förväntat resultat</u>:

Sidan sparas med&quot;leverans&quot; i URL-nyckeln.

<u>Faktiskt resultat</u>:

Du kan inte spara och ett fel visas: *Värdet som anges i fältet URL-nyckel skulle generera en URL som redan finns.*

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

Du kan inte använda termen&quot;leverans&quot; i URL-nyckeln, men du kan använda termen&quot;leverans&quot; i kombination med en annan bokstav eller siffra (till exempel&quot;leverans1&quot; och&quot;leverans2&quot;). Även om termen inte behöver vara&quot;leverans&quot;+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - termen kan vara vilken sträng som helst så länge längden inte överstiger 255 tecken.

Utför följande steg:

1. Logga in på Commerce Admin.
1. Gå till **Marknadsföring** > SEO &amp; Search > **URL-omskrivning**.
1. Klicka **Lägg till URL-omskrivning**.
1. Välj *Egen* i listrutan Skapa URL-omskrivning.
   1. Skriv i Request Path &quot;shipping&quot;. Obs! Sökvägen för begäran är den som användaren anger i webbläsaren och målsökvägen är den plats där den ska dirigeras om.
   1. Skriv den nya URL-nyckeln i målsökvägen (till exempel &quot;shipping1&quot;).
   1. Välj **Nej** i listrutan Omdirigering.

## Relaterad läsning

* [URL-omskrivning](https://docs.magento.com/user-guide/marketing/url-rewrite.html) i vår användarhandbok.
* [SEO Best Practices](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) i vår användarhandbok.
