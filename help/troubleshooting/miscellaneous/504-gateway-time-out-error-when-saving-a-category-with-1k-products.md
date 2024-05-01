---
title: 504 gatewaytimeout-fel när en kategori sparas med 1k+-produkter
description: I den här artikeln föreslås en lösning på det timeout-problem du kan ha när du utför åtgärder med stora kategorier (1k+-produkter).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# 504 gatewaytimeout-fel när en kategori sparas med 1k+-produkter

I den här artikeln föreslås en lösning på det timeout-problem du kan ha när du utför åtgärder med stora kategorier (1k+-produkter).

## Berörda produkter och versioner:

* Adobe Commerce i molninfrastruktur 2.3.3
* Adobe Commerce lokal 2.3.3
* Magento Open Source 2.3.3

## Problem

Krav: **Lager** > **Konfiguration** > **KATALOG** > **Katalog** > **Använd kategorisökväg för produkt-URL:er** option is set to *Ja* för butiksvyn.

<u>Steg som ska återskapas</u>

1. Gå till Commerce Admin **Katalog** > **Kategorier**.
1. Öppna en stor kategori, till exempel mer än 1 000 tilldelade produkter.
1. Lägg till en produkt i kategorin.
1. Klicka **Spara kategori**.

<u>Förväntat resultat:</u>

Kategorin har sparats.

<u>Faktiskt resultat:</u>

Efter fem minuters sparande visas sidan med timeout-fel för 504-gateway.

## Orsak

Processen tar längre tid än serverns konfigurerade timeout.

## Lösning

Inaktiverar **Generera URL-omskrivningar för kategori/produkt** tar bort alla omskrivningar av kategori-/produkt-URL:er från databasen och minskar avsevärt tiden som krävs för åtgärder med stora kategorier.

>[!WARNING]
>
>Om du avmarkerar det här alternativet tas återskrivningar av kategori-/produkt-URL:er bort permanent, utan möjlighet att återställa dem.

Så här inaktiverar du **Generera URL-omskrivningar för kategori/produkt** alternativ:

1. I Commerce Admin går du till **Lager** > **Konfiguration** > **KATALOG** > **Katalog**.
1. I det övre vänstra hörnet på konfigurationssidan, i **Omfång** fält, ange konfigurationsomfånget till *Standardkonfiguration*.
1. Ange **Generera URL-omskrivningar för kategori/produkt** till *Nej*.
1. Klicka **Spara konfiguration**.
1. Rensa cachen genom att köra    ```bash    bin/magento cache:clean    ```    eller i Commerce Admin under **System** > **verktyg** > **Cachehantering**.

Nu kan du lägga till produkter i kategorier eller flytta kategorier med ett stort antal produkter, och dessa åtgärder tar mycket mindre tid och bör inte orsaka timeout.

## Relaterad läsning

[Automatiska produktomdirigeringar](https://docs.magento.com/user-guide/v2.3/marketing/url-redirect-product-automatic.html) i vår användarhandbok.
