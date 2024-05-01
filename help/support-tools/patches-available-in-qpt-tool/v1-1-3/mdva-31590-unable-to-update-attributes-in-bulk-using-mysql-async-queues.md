---
title: 'MDVA-31590: Det går inte att uppdatera attribut i grupp med MySQL async-köer'
description: MDVA-31590-korrigeringen löser problemet där användarna inte kan uppdatera attribut i grupp med hjälp av MySQL async-köer. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 är installerat. Korrigerings-ID är MDVA-31590. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 57db28dd-a739-4a77-927d-6339af4fa4a6
feature: Attributes, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# MDVA-31590: Det går inte att uppdatera attribut i grupp med MySQL async-köer

MDVA-31590-korrigeringen löser problemet där användarna inte kan uppdatera attribut i grupp med hjälp av MySQL async-köer. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 är installerat. Korrigerings-ID är MDVA-31590. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användare kan inte uppdatera attribut i grupp med MySQL async.

<u>Steg som ska återskapas</u>:

1. Utför en massåtgärd för att uppdatera attributvärden för ett fåtal produkter i produktrutnätet.
   * Kontrollera produkter och välj **Uppdatera attribut** i listrutan Åtgärder.
1. Ange värden för attributen och tilldela produkter till webbplatser och spara.
1. När sidan har lästs in igen visas ett meddelande som följande:
   *Uppgiften Uppdatera attribut för N valda produkter: 1 objekt har schemalagts för en uppdatering.*
1. Vänta i några sekunder och ladda om backend-sidan.

<u>Förväntade resultat</u>:

1. Sidan visar ett meddelande om att uppdateringen lyckades, som: *1 objekt har uppdaterats.*
1. Attributvärden för relaterade produkter uppdateras.
1. I DB skapas nya poster i båda `magento_bulk` tabell och `magento_operation` tabell (åtgärder som är relaterade till massan).
1. Nya poster skapas i `queue_message` tabell (relaterat till köerna `product_action_attribute.update` och/eller `product_action_attribute.website.update`).
1. `queue_message_status` tabellen har poster med status &quot;4&quot;.
1. Det finns INGA fel i `system.log`.

<u>Faktiska resultat</u>:

1. På sidan visas fortfarande ett meddelande som följande:
   *Uppgiften Uppdatera attribut för N valda produkter: 1 objekt har schemalagts för en uppdatering.*
1. Attributvärden för produkterna uppdateras.
1. En ny post skapas i `message_bulk` tabellen, men det finns inga relaterade poster i `magento_operation` tabell.
1. Nya poster skapas i `queue_message` och `queue_message_status` tabeller.
1. `queue_message_status` tabellen har en post med felstatus (statusvärde &quot;6&quot;).
1. `system.log` innehåller fel som liknar följande:
   *main.CRITICAL: Meddelandet har avvisats: SQLSTATE[23000]: Överträdelse av integritetsbegränsning: 1048 Kolumnen operation_key får inte vara null, frågan var: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VÄRDEN (?, ?, ?, ?, ?, ?, ?, ?, ?, ?) [][]*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) -avsnitt.
