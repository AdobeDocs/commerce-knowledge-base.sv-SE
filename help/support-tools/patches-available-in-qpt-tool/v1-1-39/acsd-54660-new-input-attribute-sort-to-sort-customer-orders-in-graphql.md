---
title: 'ACSD-54660: Ny sortering av indataattribut för att sortera kundorder i [!DNL GraphQL]'
description: Använd patchen ACSD-54660 för att åtgärda Adobe Commerce-problemet där ett nytt inmatningsattribut "sort" läggs till för att sortera kundorder i [!DNL GraphQL] efter "sort_field" och "sort_direction".
feature: GraphQL, Orders
role: Admin, Developer
exl-id: 29869139-e5e2-4b00-a090-e2c6673ff9ca
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# ACSD-54660: Sortering av nya indatafält har lagts till för att sortera kundorder i [!DNL GraphQL]

Korrigeringen ACSD-54660 åtgärdar ett problem där ett nytt indataattribut åtgärdas `sort` läggs till för att sortera kundorder i [!DNL GraphQL] av `sort_field` och `sort_direction`. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 är installerat. Korrigerings-ID är ACSD-54660. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Nytt inmatningsattribut `sort` läggs till för att sortera kundorder i [!DNL GraphQL] av `sort_field` och `sort_direction`.

<u>Steg som ska återskapas</u>:

Fråga kundorder med [!DNL GraphQL]:

```
  {
    customerOrders {
      items {
        order_number
        id
        created_at
        grand_total
        status
      }
    }
  }
```

<u>Förväntade resultat</u>:

Den här korrigeringen lägger till `sort` och `sort_direction` argument till `customer.orders`.

<u>Faktiska resultat</u>:

Det går inte att sortera beställningarna med [!DNL GraphQL].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
