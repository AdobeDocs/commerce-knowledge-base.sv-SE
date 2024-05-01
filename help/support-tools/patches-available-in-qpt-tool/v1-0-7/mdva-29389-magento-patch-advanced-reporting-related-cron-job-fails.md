---
title: 'MDVA-29389: Avancerat rapportrelaterat kronjobb misslyckas'
description: '"Korrigeringen MDVA-29389 åtgärdar ett problem där det i Advanced Reporting där kronjob "analytics_collect_data" säger: "*Port måste konfigureras i värdparametern (som localhost:3306)*". Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Korrigerings-ID är MDVA-29389. Problemet har åtgärdats i Adobe Commerce 2.4.2."'
exl-id: eee909d5-9d0d-46b6-846a-665f89db0eee
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-29389: Avancerat rapportrelaterat kron-jobb misslyckas

MDVA-29389-korrigeringen åtgärdar problemet där med avancerad rapportering `analytics_collect_data` cronjob säger: &quot;*Port måste konfigureras inom värdparametern (som localhost:3306)*&quot;. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Korrigerings-ID är MDVA-29389. Problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4.

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.1.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Aktivera Avancerad rapportering i din Adobe Commerce-instans.
1. Kör följande fråga för att infoga analytiska/allmänna/tokenvärde i databasen:

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. Öppna env.php och lägg till port i värdparametern i DB-konfigurationen i följande format: `'host' => 'hostname:port',`
1. Rensa cache.
1. Kör `analytics_collect_data` cron-jobb.

<u>Förväntade resultat</u>:

The `analytics_collect_data` jobbet körs när standardport eller icke-standardport används för att ansluta till MySQL i env.php.

<u>Faktiska resultat</u>:

The `analytics_collect_data` jobbet returnerar ett fel &quot;*Port måste konfigureras inom värdparametern (som localhost:3306)*&quot; när en port som inte är standard används för att ansluta till MySQL i env.php.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
