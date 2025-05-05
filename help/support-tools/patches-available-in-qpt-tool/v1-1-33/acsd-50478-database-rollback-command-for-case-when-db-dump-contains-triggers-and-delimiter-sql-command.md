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

Korrigeringen ACSD-50478 åtgärdar JS-problemet för återställningsåtgärden i säkerhetskopieringsrutnätet och databasåterställningskommandot för ett fall när DB-dumpen innehåller utlösare och ett *delimiter*-SQL-kommando. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 har installerats. Korrigerings-ID är ACSD-50478. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

JS-problem för återställningsåtgärden i säkerhetskopieringsrutnätet och kommandot för databasåterställning för ett fall när DB-dumpen innehåller utlösare och ett *avgränsare* SQL-kommando.

<u>Steg som ska återskapas</u>:

1. Ställ in indexerare på läget [!UICONTROL Update on Schedule] så att utlösare skapas i databasen.
1. Aktivera säkerhetskopieringsfunktionen från kommandoraden:

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Gå till **System** > **Verktyg** > **Säkerhetskopior** och generera en DB-säkerhetskopia.
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

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
