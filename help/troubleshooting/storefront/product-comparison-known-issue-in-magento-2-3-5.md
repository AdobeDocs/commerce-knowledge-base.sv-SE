---
title: Produktjämförelse - känt fel i Adobe Commerce 2.3.5
description: I den här artikeln ges rekommendationer om hur du undviker ett känt [produktjämförelse](https://docs.magento.com/user-guide/marketing/product-compare.html)-problem i Adobe Commerce lokal 2.3.5 och Adobe Commerce om molninfrastruktur 2.3.5.
exl-id: 1488e2db-4a5d-4963-b48e-b84f760582d1
feature: Products, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Produktjämförelse - känt fel i Adobe Commerce 2.3.5

Den här artikeln innehåller rekommendationer om hur du undviker en känd [produktjämförelse](https://docs.magento.com/user-guide/marketing/product-compare.html) problem i Adobe Commerce 2.3.5 och Adobe Commerce om molninfrastruktur 2.3.5.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.3.5
* Adobe Commerce om molninfrastruktur 2.3.5

## Problem

När en användare försöker jämföra produkter från olika butiksvyer och en produkt har ett tomt värde för ett jämförbart attribut visas en skadad jämförelsesida i Adobe Commerce.

## Lösning

Ange värden som inte är tomma för jämförbara produktattribut eller använd standardvärdet för butiksvyn för attributet. Jämförbara attributvärden får inte vara tomma.

>[!NOTE]
>
>Produktattribut anges att användas för jämförelse med **Jämförelsebar på Storefront** konfigurationsinställning. Mer information finns i [Skapar produktattribut](https://docs.magento.com/user-guide/stores/attribute-product-create.html#step-4-describe-the-storefront-properties) i vår användarhandbok.

En programfix kommer att finnas i Adobe Commerce 2.3.6, som kommer att släppas tredje kvartalet 2020.

Du kan visa korrigeringen i GitHub (tänk på att korrigeringen inte gick igenom regressionstestning och inte är en officiell snabbkorrigering): <https://github.com/magento/magento2/pull/27662>

## Relaterad läsning

<ul><li>Adobe Commerce Support Knowledge Base-artiklar om Adobe Commerce 2.3.5:<ul>
<li>
<p title="Beställningar för flera leveranser med en virtuell produkt som inte har bearbetats korrekt i Adobe Commerce 2.3.5"><a href="/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md">Beställningar för flera leveranser med en virtuell produkt som inte har bearbetats korrekt i Adobe Commerce 2.3.5</a></p>
</li>
<li><a href="/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md">Ett problem har uppstått med produktantalet för gruppåtgärd i Adobe Commerce 2.3.5</a></li>
<li>
<p title="Problem med betalningsmetod i Adobe Commerce för molninfrastruktur och Adobe Commerce lokal 2.3.5 och 2.3.5-p1"><a href="/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md">Problem med betalningsmetod i Adobe Commerce för molninfrastruktur och Adobe Commerce lokal 2.3.5 och 2.3.5-p1</a></p>
</li>
<li>
<p title="Adobe Commerce uppmanar sina kunder att logga in, men erbjuder en ogiltig länk"><a href="/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md">Adobe Commerce uppmanar sina kunder att logga in, men erbjuder en ogiltig länk</a></p>
</li>
<li>
<p title="Patch for Amazon Pay checkout issue in Adobe Commerce 2.3.5-p1"><a href="/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md">Patch for Amazon Pay checkout issue in Adobe Commerce 2.3.5-p1</a></p>
</li>
</ul>
</li><li><a href="https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues">Adobe Commerce 2.3.5 Kända fel</a> i vår utvecklardokumentation</li></ul>
