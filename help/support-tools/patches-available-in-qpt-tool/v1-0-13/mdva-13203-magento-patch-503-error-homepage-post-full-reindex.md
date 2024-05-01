---
title: 'MDVA-13203 patch: 503 error homepage post full reindex'
description: '"Korrigeringsfilen MDVA-13203 Adobe Commerce åtgärdar ett problem där en underhållssida visas och det finns *CRITICAL: SQLSTATE\[23000\]: Integritetsbegränsningsfel* i "system.log". Korrigerings-ID är MDVA-13203. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 är installerat.'''
exl-id: 8e09010b-9aa4-4a79-b546-a24bb72e0e40
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-13203-patch: 503 error homepage post full reindex

Korrigeringsfilen MDVA-13203 Adobe Commerce åtgärdar ett problem där din webbplats visar en underhållssida och där det finns *CRITICAL: SQLSTATE\[23000\]: Överträdelse av integritetsbegränsning* fel i `system.log`. Korrigerings-ID är MDVA-13203. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 är installerat.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce om molninfrastruktur 2.2.4.

**Kompatibel med Adobe Commerce:** Adobe Commerce (alla distributionsmetoder) 2.3.0-2.4.1.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas:</u>

1. Gå till den URL som påverkas.
1. Underhållssidan visas.
1. Kontrollera att platsen inte har underhållsstatus via SSH:
   <pre> bin/magento-underhåll:status Status: underhållsläge är inte aktivt Lista över undantagna IP-adresser: ingen</pre>
1. Titta på `system.log`:

<pre>grep critical -i var/log/system.log |tail [2018-09-04 17:05:18] report.CRITICAL: SQLSTATE[23000]: Överträdelse av integritetsbegränsning: 1062 Dubblettpost 4613 för nyckeln PRIMARY, frågan var: INSERT INTO`search_tmp_5b8ebb4e994da5_80272 89` (`entity_id`,`score`) VÄRDEN (?, ?),... (?, ?), (?, ?) [] [] [2018-09-04 17:05:21] report.CRITICAL: SQLSTATE[23000]: Överträdelse av integritetsbegränsning: 1062 Dubblettpost 4613 för nyckeln PRIMARY, frågan var: INSERT INTO`search_tmp_5b8ebb5157943_523 33638` (`entity_id`,`score`) VÄRDEN (?, ?),..,(?, ?) [] [] [2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: Överträdelse av integritetsbegränsning: 1062 Dubblettpost '1350' för nyckeln 'PRIMARY', frågan var: INSERT INTO`search_tmp_5b8ebb6b7028f4_6805 024` (`entity_id`,`score`) VÄRDEN (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?), (?, ?) [] [] [2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: Överträdelse av integritetsbegränsning: 1062 Dubblettpost '1350' för nyckeln 'PRIMARY', frågan var: INSERT INTO`search_tmp_5b8ebb6b785a9_2360 993` (`entity_id`,`score`) VÄRDEN (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?), (?, ?) [] [] date Tue Sep 4 17:06:11 UTC 2018</pre>

<u>Förväntade resultat:</u> Du borde se sajten.

<u>Faktiska resultat:</u> Underhållssidan visas på grund av problem med databaskonsekvens.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
