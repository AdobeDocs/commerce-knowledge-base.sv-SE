---
title: "Adobe Commerce 2.3.6: oändlig snurra som visas när du sparar en adress"
description: I den här artikeln beskrivs ett känt Adobe Commerce 2.3.6-problem, där väntetiden visas i oändlighet när du sparar en adress i Mitt konto i butiken.
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Adobe Commerce 2.3.6: oändlig snurra som visas när adressen sparas

I den här artikeln beskrivs ett känt Adobe Commerce 2.3.6-problem, där väntetiden visas i oändlighet när du sparar en adress i Mitt konto i butiken.

## Berörda produkter och versioner

* Adobe Commerce 2.3.6 med Vertex-integrering aktiverad (endast Firefox-webbläsare)

## Problem

När du sparar en adress i Mitt kontoavsnitt i butiken visas ibland den väntande snurren i oändlighet på grund av ett fel i Vertex core-JS.

## Tillfällig lösning

Tillfällig lösning: använd en annan webbläsare än Firefox.

Problemet har åtgärdats i Adobe Commerce 2.3.1.

## Relaterad läsning

* [Olika adresser tillåts inte när &#39;Min fakturerings- och leveransadress är densamma&#39; avmarkeras med VertexAddress Cleansing](/help/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.md) i vår kunskapsbas för support.
* [Adobe Commerce 2.4.1 Vertex Address validation message post address update](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) i vår kunskapsbas för support.
