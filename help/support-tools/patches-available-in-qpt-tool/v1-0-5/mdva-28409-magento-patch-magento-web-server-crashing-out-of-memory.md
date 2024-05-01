---
title: 'MDVA-28409-korrigering: Adobe Commerce webbserver kraschar - slut på minne'
description: MDVA-28409-korrigeringen åtgärdar ett problem där cron-jobbet för att ta bort citattecken stoppades på grund av att ett stort antal objekt måste bearbetas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5 är installerat.
exl-id: 175e5f2f-2f76-42ee-83e9-c1b23ff81e96
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-28409-korrigering: Adobe Commerce webbserver kraschar - slut på minne

MDVA-28409-korrigeringen åtgärdar ett problem där cron-jobbet för att ta bort citattecken stoppades på grund av att ett stort antal objekt måste bearbetas. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5 är installerat.

## Berörda produkter och versioner

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.4 - 2.3.5, 2.4.0

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Problemet är att cron-jobbet har slut på minne på grund av mängden data som jobbet försöker bearbeta. Symtomen på det här problemet är bland annat långsamma prestanda på grund av hög diskanvändning av MySQL och lågt webbserverminne.

<u>Steg som ska återskapas:</u>

Om du vill kontrollera om det finns ett cron-jobb som inte kan ta bort föråldrade citattecken kör du följande fråga:

```
select * from cron_schedule where job_code like '%sales_clean_quotes%'
```

<u>Förväntat resultat:</u>

Status för `sales_clean_quotes` cron-jobb ska `success`.

<u>Faktiskt resultat:</u>

Status för `sales_clean_quotes` cron job is `running` eller `error`.

Ett annat sätt att bekräfta att det finns ett cron-jobb som inte kan ta bort föråldrade citattecken är att mappa utdata från frågan från **Steg 1** (`executed_at`) mot tidsstämpeln för eventuella minnesfel i `/var/log/cron.log`. Om det finns ett cron-jobb som inte kan bearbeta mängden data kan du se ett meddelande som liknar:

```
PHP Fatal error:  Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91

Fatal error: Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91
--
[2020-05-30 05:00:27.224718] Launching command 'php bin/magento cron:run'.
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) -avsnitt.
