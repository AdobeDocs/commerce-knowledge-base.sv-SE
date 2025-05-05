---
title: 504 gatewaytimeout-fel när en kategori sparas med 1k+-produkter
description: I den här artikeln föreslås en lösning på det timeout-problem du kan ha när du utför åtgärder med stora kategorier (1k+-produkter).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Förutsättningar: Alternativet **Lagrar** > **Konfiguration** > **KATALOG** > **Katalog** > **Använd kategorisökväg för produkt-URL:er** är *Ja* för din butiksvy.

<u>Steg som ska återskapas</u>

1. Gå till **Katalog** > **Kategorier** i Commerce Admin.
1. Öppna en stor kategori, till exempel mer än 1 000 tilldelade produkter.
1. Lägg till en produkt i kategorin.
1. Klicka på **Spara kategori**.

<u>Förväntat resultat:</u>

Kategorin har sparats.

<u>Faktiskt resultat:</u>

Efter fem minuters sparande visas sidan med timeout-fel för 504-gateway.

## Orsak

Processen tar längre tid än serverns konfigurerade timeout.

## Lösning

Om du inaktiverar alternativet **Skapa omskrivningar av kategori/produkt** tas alla återskrivningar av kategori-/produkt-URL bort från databasen, vilket minskar tiden som krävs för åtgärder med stora kategorier avsevärt.

>[!WARNING]
>
>Om du avmarkerar det här alternativet tas återskrivningar av kategori-/produkt-URL:er bort permanent, utan möjlighet att återställa dem.

Så här inaktiverar du alternativet **Skapa URL-omskrivningar för kategori/produkt**:

1. Gå till **Lagrar** > **Konfiguration** > **KATALOG** > **Katalog** i Commerce Admin.
1. I konfigurationsidans övre vänstra hörn anger du konfigurationsomfånget till *Standardkonfiguration* i fältet **Scope**.
1. Ange **Generera URL-omskrivningar för kategori/produkt** till *Nej*.
1. Klicka på **Spara konfiguration**.
1. Rensa cachen genom att köra    ```bash    bin/magento cache:clean    ```    eller i Commerce Admin under **System** > **Verktyg** > **Cachehantering** .

Nu kan du lägga till produkter i kategorier eller flytta kategorier med ett stort antal produkter, och dessa åtgärder tar mycket mindre tid och bör inte orsaka timeout.

## Relaterad läsning

[Automatiska produktomdirigeringar](https://experienceleague.adobe.com/sv/docs/commerce-admin/marketing/seo/url-rewrites/url-redirect-product-automatic) i användarhandboken.
