---
title: 'MDVA-34847: customer_grid_flat table slow queries'
description: MDVA-34847-korrigeringen löser problemet med långsamma frågor i tabellen "customer_grid_flat". Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
exl-id: e91cb86d-83cd-4267-a132-64465a57da7f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-34847: customer_grid_flat table slow queries

MDVA-34847-korrigeringen löser problemet med långsamma frågor i tabellen `customer_grid_flat`. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce i molninfrastruktur 2.3.3

**Kompatibel med Adobe-versioner:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Långsamma frågor förekommer i tabellen `customer_grid_flat`.

<u>Steg som ska återskapas</u>:

1. Skapa en Admin-användare med ett anpassat omfång (Exempel: Ange **GWS** = *0,* och välj den befintliga standardwebbplatsen med **ID** = *1*).
1. Skapa alla produkt- och kategoriartiklar.
1. Placera en order från förgrunden.
1. Logga in som ny användare i Admin.
1. Gå till försäljningsrutnätet (**Försäljning > Beställningar**).
1. Kontrollera att SQL-frågan har skickats till DB (databas).

<u>Förväntade resultat</u>:

GWS-tillägget för administratörer bör använda

```sql
int
```

värden för

```sql
website_id
```

i SQL-villkor, som förväntat, som:

```sql
main_table.website_id IN (1)
```

<u>Faktiska resultat</u>:

Admin GWS-tillägget lade till ett villkor med

```sql
website_id
```

värde som

```sql
string
```

, som:

```sql
main_table.website_id IN ('1')
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
