---
title: 'MDVA-43348: Fel i GraphQL-begäran med presentkort'
description: Korrigeringen MDVA-43348 åtgärdar ett fel där en GraphQL-begäran med presentkort visar ett fel om "present_card_options" innehåller "uid". Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-43348. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: a9c0e1da-6698-463a-a6a8-60522f029b53
feature: Gift, GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# MDVA-43348: Fel i GraphQL-begäran med presentkort

MDVA-43348-korrigeringen åtgärdar ett problem där en GraphQL-begäran med presentkort visar ett fel om `gift_card_options` innehåller &quot;uid&quot;. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-43348. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel visas om present_card_options innehåller &quot;uid&quot;.

<u>Steg som ska återskapas</u>:

1. Skapa ett presentkort.
1. Utför omindexering.
1. Ring GraphQL där URL-nyckeln är &quot;presentkort&quot;:

<pre>
<code class="language-graphql">
query getProductOptionsForProductPage_bypassFastly($urlKey: String!) &lbrace;
  products(filter: { url_key: { eq: $urlKey } }) &lbrace;
    items &lbrace;
      id
      url_key
      ... on GiftCardProduct &lbrace;
        allow_open_amount
        open_amount_min
        open_amount_max
        giftcard_type
        is_redeemable
        lifetime
        allow_message
        message_max_length
        gift_card_options &lbrace;
          uid
          title
          required
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Förväntade resultat</u>:

Presentkortsdata returneras på begäran.

<u>Faktiska resultat</u>:

Följande fel inträffar vid begäran om presentkortsdata:

<pre>
<code class="language-graphql">
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        0,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        1,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        2,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        3,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        4,
        "uid"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "products": &lbrace;
      "items": &lbrack;
        &lbrace;
          "id": 2,
          "url_key": "gitf-card",
          "allow_open_amount": false,
          "open_amount_min": null,
          "open_amount_max": null,
          "giftcard_type": "VIRTUAL",
          "is_redeemable": true,
          "lifetime": 0,
          "allow_message": true,
          "message_max_length": 255,
          "gift_card_options": &lbrack;
            null,
            null,
            null,
            null,
            null
          &rbrack;
        &rbrace;
      &rbrack;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
