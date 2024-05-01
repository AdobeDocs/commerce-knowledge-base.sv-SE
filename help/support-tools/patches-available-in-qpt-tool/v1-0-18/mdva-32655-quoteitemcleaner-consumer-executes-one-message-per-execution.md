---
title: 'MDVA-32655: "quoteItemCleaner"-konsument kör ett meddelande per körning'
description: Korrigeringen MDVA-32655 åtgärdar den felaktiga statusen för "pågående" meddelande till korrekt "slutfört" meddelande för "quoteItemCleaner" efter att flera produkter har tagits bort. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Korrigerings-ID är 32655. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 07213430-f779-4a53-89fd-bc3905e13675
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32655: &quot;quoteItemCleaner&quot;-konsument kör ett meddelande per körning

Korrigeringen MDVA-32655 åtgärdar den felaktiga statusen för &quot;pågående&quot; meddelande till rätt &quot;slutförda&quot; meddelande för konsumenten `quoteItemCleaner` efter att flera produkter har tagits bort. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Korrigerings-ID är 32655. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.3.3

**Kompatibel med Adobe Commerce:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The `quoteItemCleaner` konsument kör endast ett meddelande vid varje körning.

<u>Steg som ska återskapas</u>:

1. Kontrollera `queue_message_status` databastabell och se till att alla befintliga kömeddelanden är i läget &quot;Slutför&quot; (status-ID 4).
1. Stoppa automatisk körning av Adobe Commerce cron.
1. Skapa två eller tre enkla produkter.
1. Gör en massborttagning av dessa tre enkla produkter.
1. I `queue_message_status` tabellen ser du att det finns tre nya poster för `catalog_product_removed_queue` ämne med status-ID 2 (ny post).
1. Kör följande kommando för att bearbeta de väntande `catalog_product_removed_queue` meddelanden:

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u>Förväntade resultat</u>:

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

Alla `catalog_product_removed_queue` meddelandestatus uppdateras till slutförd (ID=4).

<u>Faktiska resultat</u>:

Endast en post av de tre uppdateras till statusen&quot;Fullständig&quot; (ID = 4). Status för de andra två meddelandena är status-ID = 3 (pågående). En eftersläpning genereras med obearbetade kömeddelanden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
