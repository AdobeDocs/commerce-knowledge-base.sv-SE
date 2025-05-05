---
title: Kan inte spara *kontakt* som URL-nyckel
description: I den här artikeln finns en lösning på problemet när du inte kan spara *contact* som URL-nyckel (t.ex. "/contact") för produkter eller CMS-sidor. När du försöker spara URL-nyckeln visas ett fel som anger att URL-nyckeln är en dubblett-URL.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Det går inte att spara *kontakt* som URL-nyckel

I den här artikeln finns en lösning på problemet när du inte kan spara *contact* som en URL-nyckel (t.ex. &quot;/contact&quot;) för produkter eller CMS-sidor.

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.4.x

## Problem

Du kan inte spara en produkt eller en CMS-sida med termen *contact* som URL-nyckel. När du försöker spara URL-nyckeln visas ett fel som anger att URL-nyckeln är en dubblett-URL.

<u>Steg som ska återskapas</u>:

Skapa en CMS-sida med *contact* som URL-nyckel.

<u>Förväntat resultat</u>:

Sidan sparas med *contact* som URL-nyckel.

<u>Faktiskt resultat</u>:

Du kan inte spara sidan. Du får felet: *Värdet som anges i fältet URL-nyckel skulle generera en URL som redan finns.*

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

Du kan inte använda termen *contact* som URL-nyckel, men du kan använda termen *contact* i kombination med en annan bokstav eller siffra (till exempel *contact1* och *contact2*). Även om termen inte behöver vara *contact+\&lt;ett annat tal eller en annan bokstav\>*, kan termen vara vilken sträng som helst så länge längden inte överstiger 255 tecken.

Utför följande steg:

1. Logga in på Commerce Admin.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Klicka på **[!UICONTROL Add URL Rewrite]**.
1. Välj *[!UICONTROL Custom]* i listrutan [!UICONTROL Create URL Rewrite].
   1. Skriv &quot;contact&quot; i [!UICONTROL Request Path]. Observera att [!UICONTROL Request Path] är det som en användare anger i webbläsaren och att [!UICONTROL Target Path] är den plats där den ska dirigeras om.
   1. I [!UICONTROL Target Path] skriver du in den nya URL-nyckeln (till exempel &quot;contact1&quot;).
   1. Välj *[!UICONTROL No]* i listrutan [!UICONTROL Redirect].

## Relaterad läsning

* [URL-omskrivningar](https://experienceleague.adobe.com/sv/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite) i användarhandboken.
* [SEO Best Practices](https://experienceleague.adobe.com/sv/docs/commerce-admin/marketing/seo/seo-overview) i vår användarhandbok.
