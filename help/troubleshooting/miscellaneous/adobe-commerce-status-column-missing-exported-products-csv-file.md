---
title: Adobe Commerce statuskolumn saknar exporterad produkt, CSV-fil
description: Den här artikeln innehåller en lösning på problemet när du inte hittar statuskolumnen i CSV-filen som innehåller exporterade produkter.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce statuskolumn saknar exporterad produkt, CSV-fil

Den här artikeln innehåller en lösning på problemet när du inte kan hitta statuskolumnen (d.v.s. ange om produkten är aktiverad eller inaktiverad) i CSV-filen som innehåller exporterade produkter. Produktens status anges av kolumnen [!UICONTROL product_online].

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) alla [versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Du kan inte hitta kolumnen [!UICONTROL status] i CSV-filen som innehåller exporterade produkter. Du kan till exempel exportera en CSV-fil med alla SKU:er, med status, men tabellen verkar sakna kolumnen [!UICONTROL status].

<u>Steg att återskapa:</u>

1. I Adobe Commerce Admin väljer du **[!UICONTROL System]** under **[!UICONTROL Data Transfer]** select **[!UICONTROL Export]**.
1. I avsnittet **[!UICONTROL Export Settings]** väljer du i listrutan **[!UICONTROL Entity Type]** **[!UICONTROL Products]**.
1. Sök efter **[!UICONTROL status]**, visas under **[!UICONTROL Attribute Code]**. Attributkoden visas i listan med tillgängliga attribut (**[!UICONTROL Enable Product]**).
1. Klicka på **[!UICONTROL Export]**.

<u>Förväntat resultat:</u>

I CSV-filen som du just exporterade visas en kolumn med namnet [!UICONTROL status].

<u>Faktiskt resultat:</u>

Du ser ingen kolumn med namnet [!UICONTROL status] i den exporterade CSV-filen.

## Orsak

Produktens statusattribut har bytt namn i CSV-filen. Det är nu kolumnen [!UICONTROL product_online].

## Lösning

1. Välj **[!UICONTROL System]**, under **[!UICONTROL Data Transfer]** select **[!UICONTROL Import]**.
1. Klicka på **[!UICONTROL Download Sample File]**.
1. Du kan se kolumnen [!UICONTROL product_online] i CSV-filen.

## Relaterad läsning

* [Arbeta med CSV-filer](https://docs.magento.com/user-guide/system/data-csv.html) i vår användarhandbok.
* [Referens för produktexportattribut](https://docs.magento.com/user-guide/system/data-attributes-product.html) i användarhandboken.
