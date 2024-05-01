---
title: Kan inte spara *kontakt* som URL-nyckel
description: I den här artikeln finns en lösning på problemet när du inte kan spara *contact* som en URL-nyckel (t.ex. "/contact") för produkter eller CMS-sidor. När du försöker spara URL-nyckeln visas ett fel som anger att URL-nyckeln är en dubblett-URL.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Kan inte spara *kontakta* som URL-tangenten

I den här artikeln finns en lösning på problemet när du inte kan spara *kontakta* som en URL-nyckel (t.ex. &quot;/contact&quot;) för produkter eller CMS-sidor.

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.4.x

## Problem

Du kan inte spara en produkt eller en CMS-sida med termen *kontakta* som URL-nyckel. När du försöker spara URL-nyckeln visas ett fel som anger att URL-nyckeln är en dubblett-URL.

<u>Steg som ska återskapas</u>:

Skapa en CMS-sida med *kontakta* som URL-nyckel.

<u>Förväntat resultat</u>:

Sidan sparas med *kontakta* som URL-nyckel.

<u>Faktiskt resultat</u>:

Du kan inte spara sidan. Du får felmeddelandet: *Värdet som anges i fältet URL-nyckel skulle generera en URL som redan finns.*

## Orsak

*Kontakt* är ett reserverat ord som definieras i `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## Lösning

Du kan inte använda termen *kontakta* som URL-nyckel kan du dock använda termen *kontakta* kombinerat med en annan bokstav eller siffra (till exempel *contact1* och *kontakt2*). Även om termen inte behöver vara *contact+\&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;>* kan termen vara vilken sträng som helst så länge längden inte överstiger 255 tecken.

Utför följande steg:

1. Logga in på Commerce Admin.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Klicka på **[!UICONTROL Add URL Rewrite]**.
1. Välj *[!UICONTROL Custom]* på [!UICONTROL Create URL Rewrite] nedrullningsbar meny.
   1. I [!UICONTROL Request Path], skriver du &quot;contact&quot;. Observera att [!UICONTROL Request Path] är vad en användare skriver i webbläsaren och [!UICONTROL Target Path] är den plats där den ska omdirigeras till.
   1. I [!UICONTROL Target Path]skriver du den nya URL-nyckeln (till exempel &quot;contact1&quot;).
   1. Välj *[!UICONTROL No]* i [!UICONTROL Redirect] nedrullningsbar meny.

## Relaterad läsning

* [URL-omskrivning](https://docs.magento.com/user-guide/marketing/url-rewrite.html) i vår användarhandbok.
* [SEO Best Practices](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) i vår användarhandbok.
