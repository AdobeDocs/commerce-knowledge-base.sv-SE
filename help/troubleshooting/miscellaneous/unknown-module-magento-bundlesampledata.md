---
title: Okänd modul Magento_BundleSampleData
description: I den här artikeln finns en korrigering för det okända modulfelet vid installation av Adobe Commerce.
exl-id: c927bc8f-d70b-4305-87c1-223001212555
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Okänd modul Magento_BundleSampleData

I den här artikeln finns en korrigering för det okända modulfelet vid installation av Adobe Commerce.

## Problem {#details}

Under installationen visas ett meddelande som liknar följande:

```text
[ERROR] exception 'LogicException' with message 'Unknown module in the requested list: 'Magento_BundleSampleData''
```

## Lösning {#solution}

Prova något av följande i taget och försök sedan installera igen.

1. Kör webbinstallationsguiden. Modulerna listas i  **Konfigurationer av avancerade moduler**. Så här inaktiverar du **Magento\_BundleSampleData** modul, rensa **Magento\_BundleSampleData** som bilden nedan visar.

   ![tshot_bundlesampledata.png](assets/tshoot_bundlesampledata.png)

1. Rensa all webbläsarhistorik och alla data från webbläsaren.
1. Om du har Chrome tar du bort alla webbläsardata som är relaterade till din plats.  Gå till **Inställningar** > **Avancerade alternativ** > **Integritet** > **Innehållsinställningar** > **Alla cookies och webbplatsdata**. Klicka på adressen till Adobe Commerce-servern i kolumnen Plats och klicka sedan på **Ta bort alla**.
