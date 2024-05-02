---
title: 'ACSD-56741: Felsöka databaskonfigurationsfel med anpassade MySQL-utlösare'
description: Använd korrigeringsfilen ACSD-56741 för att åtgärda Adobe Commerce-problemet där ett felmeddelande *Ett försök att få åtkomst till matrisförskjutning för värdet av typen null* visas under "setup:upgrade" på grund av en anpassad MySQL-utlösare i databasen som inte hör till indexering och [!DNL MView].
feature: Install
role: Admin, Developer
source-git-commit: 216ce1035584e4c049029073ee0017d3616cdbd6
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56741: Felsöka databaskonfigurationsfel med anpassade MySQL-utlösare

Korrigeringen ACSD-56741 åtgärdar ett problem där ett felmeddelande visas *Försöker få åtkomst till matrisförskjutning på värdet av typen null* visas under `setup:upgrade` på grund av en anpassad MySQL-utlösare i databasen som inte är relaterad till indexering och [!DNL MView]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 är installerat. Korrigerings-ID är ACSD-56741. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett felmeddelande *Försöker få åtkomst till matrisförskjutning på värdet av typen null* visas under `setup:upgrade` på grund av en anpassad MySQL-utlösare i databasen som inte är relaterad till indexering och [!DNL MView].

<u>Steg som ska återskapas</u>:

1. Kör `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Kör `php bin/magento c:f`.
1. Kör `php bin/magento setup:upgrade`.

<u>Förväntade resultat</u>:

Installationsuppgraderingen avslutas utan fel.

<u>Faktiska resultat</u>:

Installationsuppgraderingen avslutas med ett felmeddelande:

*Varning: Försöker få åtkomst till matrisförskjutning för värdet av typen null*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
