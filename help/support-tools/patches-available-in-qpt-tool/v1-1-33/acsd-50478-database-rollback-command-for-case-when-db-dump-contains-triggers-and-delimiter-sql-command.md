---
title: 'ACSD-50478: JS-problem för återställningsåtgärd i säkerhetskopieringsrutnät och kommandot för databasåterställning'
description: Använd patchen ACSD-50478 för att åtgärda JS-problemet för återställningsåtgärden i säkerhetskopieringsrutnätet och kommandot för databasåterställning för ett fall när DB-dumpen innehåller utlösare och ett *delimiter* SQL-kommando.
exl-id: 8b516705-29be-462e-b3ec-3a339b6e8006
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-50478: JS-problem för återställningsåtgärd i säkerhetskopieringsrutnät och kommandot för databasåterställning

Korrigeringen ACSD-50478 åtgärdar JS-problemet för återställningsåtgärden i säkerhetskopieringsrutnätet och kommandot för databasåterställning för ett fall när DB-dumpen innehåller utlösare och en *delimiter* SQL-kommando. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 är installerat. Korrigerings-ID är ACSD-50478. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

JS-problem för återställningsåtgärden i säkerhetskopieringsrutnätet och kommandot för databasåterställning för ett fall när DB-dumpen innehåller utlösare och en *delimiter* SQL-kommando.

<u>Steg som ska återskapas</u>:

1. Ställ in indexerare på [!UICONTROL Update on Schedule] så att utlösare skapas i databasen.
1. Aktivera säkerhetskopieringsfunktionen från kommandoraden:

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Gå till **System** > **verktyg** > **Säkerhetskopior** och generera en DB-säkerhetskopia.
1. Öppna webbläsarkonsolen. Följande fel visas:

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. Försök importera databasen från kommandoraden:

   `bin/magento setup:rollback --db-file="<filename>"`

1. Följande fel visas:

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>Förväntade resultat</u>:

Databasåterställningen har slutförts både från Admin och kommandoraden.

<u>Faktiska resultat</u>:

Du observerade felen som nämns i steg 4 och steg 6.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
