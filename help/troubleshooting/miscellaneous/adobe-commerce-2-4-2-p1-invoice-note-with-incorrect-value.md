---
title: "Adobe Commerce 2.4.2-p1: fakturafaktura med felaktigt värde"
description: I den här artikeln beskrivs ett känt problem med Adobe Commerce 2.4.2-p1 där en fakturafaktura med felaktigt värde genereras när kundgruppen ändras när ordern skapas. Problemet åtgärdas i version 2.4.3.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Adobe Commerce 2.4.2-p1: fakturafaktura med felaktigt värde

I den här artikeln beskrivs ett känt problem med Adobe Commerce 2.4.2-p1 där en fakturafaktura med felaktigt värde genereras när kundgruppen ändras när ordern skapas. Problemet åtgärdas i version 2.4.3.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.2-p1
* Adobe Commerce om molninfrastruktur 2.4.2-p1

## Problem

När kundgruppen ändras när ordern skapas, genereras fakturan med en felaktig faktura.

<u>Steg som ska återskapas</u>:

1. Skapa ett **testkundskonto** och lägg till det i **butikskundgruppen**.
1. Skapa en **ny beställning** för testkunden, lägg till **Produkt** och **Adress**.
1. Välj **Leveransmetod**.
1. I avsnittet **Kontoinformation** ändrar du kundgrupp från **Återförsäljare** till **Offentlig sektor**.
1. Klicka på **Montera order**.
1. Klicka på **Faktura** > **Skicka faktura**.

<u>Förväntade resultat</u>:

Följande anteckning ska visas under avsnittet **Anteckningar för den här ordern**: &quot;Vertex Invoice sent successfully. Belopp: $0,00.&quot;

<u>Faktiska resultat</u>:

Följande anteckning visas under avsnittet **Anteckningar för den här ordern**: &quot;Vertex Invoice sent successfully. Belopp: 3,23 USD.&quot;

## Lösning

Problemet åtgärdas i version 2.4.3.
