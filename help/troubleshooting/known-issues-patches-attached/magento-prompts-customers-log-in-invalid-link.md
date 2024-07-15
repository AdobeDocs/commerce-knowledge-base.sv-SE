---
title: Adobe Commerce uppmanar sina kunder att logga in med ogiltig länk
description: Artikeln innehåller en länk till patchen för ett känt Adobe Commerce 2.3.5-problem, där kunderna uppmanas att logga in, men länken för att skicka bekräftelsemeddelandet igen fungerar inte.
exl-id: 8adef44f-56a6-4f57-a9b5-fb8583d8ae8d
feature: Logs
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce uppmanar sina kunder att logga in med ogiltig länk

Artikeln innehåller en länk till patchen för ett känt Adobe Commerce 2.3.5-problem, där kunderna uppmanas att logga in, men länken för att skicka bekräftelsemeddelandet igen fungerar inte.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) 2.3.5

## Problem

Adobe Commerce uppmanar kunderna att logga in genom att visa följande meddelande: *Det här kontot är inte bekräftat. Klicka här för att skicka bekräftelsemeddelandet igen*. Länken **Klicka här** bör öppna länksidan Skicka-bekräftelse, men den är inaktiv.

## Lösning

En korrigering för det här problemet finns i Adobe Commerce Technical Resources: [Skicka e-postlänksfelkorrigering för kontobekräftelse igen för Adobe Commerce 2.3.5](https://magento.com/tech-resources/download?_ga=2.193540264.409362045.1590506265-807369446.1578680711#download2368). En permanent programfix kommer att finnas i Adobe Commerce 2.3.6, som kommer att släppas 4:e kvartalet 2020.

Se [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner om hur du använder en dispositionsruta.

## Relaterad läsning

Artiklar i vår kunskapsbas för support och dokumentation för utvecklare om kända problem i Adobe Commerce 2.3.5:

* [Adobe Commerce 2.3.5: Problem med beställningar av virtuella produkter för flera leveranser](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
* [Produktjämförelse - känt fel i Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5, 2.3.5-p1 patch: landbetalningsproblem](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce uppmanar sina kunder att logga in med ogiltig länk](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Ett problem har uppstått med produktantalet för gruppåtgärd i Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Patch for Amazon Pay checkout issue in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
* [Kända fel i Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
