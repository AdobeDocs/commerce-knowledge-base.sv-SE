---
title: Användare kan inte lägga till produkten i kundvagnen om inget har valts i Tillåt länder
description: I den här artikeln finns en patch för det kända Adobe Commerce 2.4.4-problemet med PHP 8.1 där användare inte kan lägga till produkter i varukorgen om Tillåt länder inte är valt.
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Användare kan inte lägga till produkten i kundvagnen om inget har valts i Tillåt länder

I den här artikeln finns en patch för det kända Adobe Commerce 2.4.4-problemet med PHP 8.1 där användare inte kan lägga till produkter i varukorgen om Tillåt länder inte är valt.

## Berörda produkter och versioner

Adobe Commerce 2.4.4 med PHP 8.1

## Problem

Användarna kan inte lägga till produkter i kundvagnen om alternativet Tillåt länder är avmarkerat.

<u>Steg som ska återskapas</u>:

1. Logga in på Commerce Admin.
1. Gå till **Store** > **Configuration** > **General** > **Country options**
1. Avmarkera alla alternativ i fältet **Tillåt länder**.
1. Klicka på **Spara konfiguration** för att spara konfigurationen.
1. Gå till butiken och prova att lägga till en produkt i kundvagnen.

<u>Förväntat resultat:</u>

Du kan lägga till en produkt i kundvagnen.

<u>Faktiskt resultat:</u>

Du kan inte lägga till en produkt i kundvagnen. Följande konsolfel visas:

```bash
Failed to load resource: the server responded with a status of 400 (Bad Request)
customer-data.js:87 Uncaught Error: [object Object]
    at Object.<anonymous> (customer-data.js:87:23)
    at fire (jquery.js:3500:50)
    at Object.fireWith [as rejectWith] (jquery.js:3630:29)
    at done (jquery.js:9798:30)
    at XMLHttpRequest.<anonymous> (jquery.js:10057:37)
```

## Orsak

Adobe Commerce-konfigurationen hämtar `null` om en flervalskonfiguration inte har några markerade objekt. Den här konfigurationen kan bearbetas ytterligare i PHP-versioner tidigare än 8.1. I PHP 8.1 fungerar den dock inte korrekt på grund av de fel som orsakas av att [Deprecate skickar null till argument som inte kan ha värdet null för interna funktioner i PHP 8.1](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg).

## Lösningar

Åtgärda problemet genom att installera följande patch:

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Användbara länkar

[Använd anpassade korrigeringar för Adobe Commerce i molninfrastrukturen](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html) i vår utvecklardokumentation.
