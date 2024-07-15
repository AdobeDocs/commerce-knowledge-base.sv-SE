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

1. Kör webbinstallationsguiden. Moduler visas i **Konfigurationer av avancerade moduler**. Om du vill inaktivera modulen **Magento\_BundleSampleData** avmarkerar du kryssrutan **Magento\_BundleSampleData** enligt bilden nedan.

   ![tshot_bundlesampledata.png](assets/tshoot_bundlesampledata.png)

1. Rensa all webbläsarhistorik och alla data från webbläsaren.
1. Om du har Chrome bör du rensa alla webbläsardata som är relaterade till din webbplats.  Gå till **Inställningar** > **Avancerade alternativ** > **Sekretess** > **Innehållsinställningar** > **Alla cookies och webbplatsdata**. Klicka på Adobe Commerce-serverns adress i kolumnen Plats och klicka på **Ta bort alla**.
