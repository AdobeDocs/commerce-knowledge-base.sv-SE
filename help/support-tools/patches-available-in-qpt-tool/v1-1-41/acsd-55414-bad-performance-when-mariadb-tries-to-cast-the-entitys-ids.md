---
title: 'ACSD-55414: Dåliga prestanda när MariaDB försöker byta ut entitys_ids'
description: Använd korrigeringsfilen ACSD-55414 för att åtgärda Adobe Commerce-problemet när MariaDB försöker konvertera "entitys_ids" från sträng till heltal, vilket förhindrar prestandan vid omindexering.
feature: Attributes
role: Admin, Developer
exl-id: 008a4fda-5d80-47e2-8fb4-c1e39d15a6ba
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-55414: Dåliga prestanda när MariaDB försöker byta ut `entitys_ids`

Korrigeringsfilen ACSD-55414 åtgärdar ett problem där prestandan för omindexering hämmas när MariaDB försöker konvertera `entitys_ids` från sträng till heltal. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.41 är installerat. Korrigerings-ID är ACSD-55414. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Omindexeringens prestanda hindras när MariaDB försöker byta ut `entitys_ids` från sträng till heltal.

<u>Steg som ska återskapas</u>:

1. Uppdatera `setup/performance-toolkit/profiles/ce/small.xml` genom att konfigurera *50000* enkla produkter.
1. Generera den här profilen genom att köra kommandot: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Kör omindexering: `bin/magento indexer:reindex catalog_product_attribute`.

<u>Förväntade resultat</u>:

Omindexeringen tar rimlig tid att slutföra.

<u>Faktiska resultat</u>:

Indexeringen tar för lång tid att slutföra.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
