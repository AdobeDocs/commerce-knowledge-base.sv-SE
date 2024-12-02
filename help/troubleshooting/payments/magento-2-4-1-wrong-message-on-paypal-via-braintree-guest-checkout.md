---
title: 'Adobe Commerce 2.4.1: fel meddelande i PayPal-Braintree gästutcheckning'
description: I den här artikeln beskrivs ett känt Adobe Commerce 2.4.1-problem där en gästkund som försöker göra en beställning med PayPal via Braintree får ett felmeddelande som inte är informativt om det är inaktiverat.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: fel meddelande i PayPal-Braintree gästutcheckning

I den här artikeln beskrivs ett känt Adobe Commerce 2.4.1-problem där en gästkund som försöker göra en beställning med PayPal via Braintree får ett felmeddelande som inte är informativt om det är inaktiverat.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0, 2.4.1
* Adobe Commerce om molninfrastruktur 2.4.0, 2.4.1

## Problem

Ett ospecifikt fel visas när utcheckning av gäst inaktiveras från serverdelen och betalningsalternativet PayPal via Braintree väljs från Mini-cart eller Kundvagn.

<u>Förutsättningar</u>:

1. I Commerce Admin ställer du in **Tillåt gästutcheckning** = *Nej **under**Lagrar* > **Konfiguration** > **Försäljning** > **Utcheckning**.
1. Aktivera PayPal via Braintree enligt beskrivningen i [Braintree](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/braintree?) i användarhandboken.

<u>Steg som ska återskapas</u>:

1. Lägg produkten i varukorgen som gäst.
1. Välj **Mini-cart** och klicka på **Betala med PayPal**.
1. Slutför utcheckningen av PayPal så hamnar du på sidan för beställningsgranskning.
1. Välj **Leveransmetod**.
1. Klicka på **Montera order**.

<u>Förväntade resultat</u>:

När en kund klickar på PayPal-knappen på Mini-cart- eller Shopping Cart-sidan ska följande meddelande visas för kunden:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

Om du aktiverar direktbetalning utan att använda Braintree fungerar det här scenariot annorlunda. Gästanvändaren kan inte fortsätta med betalningsprocessen. Följande meddelande visas när gästanvändaren klickar på PayPal-knappen i minikorgen:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>Faktiska resultat</u>:

Kunden dirigeras om till kundvagnssidan och följande meddelande visas:

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## Tillfällig lösning

Lösningen på problemet är att kunden kan logga in på en butik (inloggade användare använder inte gästutcheckning) där gästutcheckning är inaktiverad. Problemet har åtgärdats i Adobe Commerce version 2.4.2.

## Relaterad läsning

* [Bästa praxis för antal produkter i kundvagn i Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048550332) i vår kunskapsbas för support.
* [Beställningsexempel: Steg 1. Lägg till artiklar i kundvagnen ](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-add-items/) i utvecklardokumentationen
* [GraphQL självstudiekurs: Steg 1. Lägg till produkter i kundvagnen ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) i utvecklardokumentationen
