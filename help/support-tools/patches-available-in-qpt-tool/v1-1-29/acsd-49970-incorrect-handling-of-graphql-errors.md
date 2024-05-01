---
title: 'ACSD-49970: Felaktig hantering av GraphQL-fel'
description: Använd korrigeringsfilen ACSD-49970 för att åtgärda Adobe Commerce-problemet där GraphQL-fel hanteras felaktigt när [!UICONTROL New Relic Reporting] är påslagen.
exl-id: 70acade5-02a5-4769-86e2-5c566b2af709
feature: GraphQL, Observability
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49970: Felaktig hantering av GraphQL-fel

Korrigeringen ACSD-49970 åtgärdar ett problem där GraphQL-fel hanteras felaktigt när *[!UICONTROL New Relic Reporting]* är påslagen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 är installerat. Korrigerings-ID är ACSD-49970. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`GraphQLOperationNames` nyckeln hanteras inte korrekt om `logDataHelper` innehåller den här nyckeln eller inte.

<u>Steg som ska återskapas</u>:

1. Kör `bin/magento deploy:mode:set developer`.
1. Logga in på Admin.
1. Aktivera **[!UICONTROL New Relic Integration]** från **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(Obs! Även om ett fel visas som anger att [!DNL New Relic] tillägget är inte tillgängligt, konfigurationen sparas).
1. Kör det här *GraphQL* mutation till `http://yourMagentoDomain/graphql` från *[!DNL Altair]* klienten eller någon annan klient eller via cURL.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Obs! Ange **[!UICONTROL Header]** till [!UICONTROL Content-Currency:CA] innan den körs).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Förväntade resultat</u>:

Det finns inga *500 undantag* i loggar, `GraphQLOperationNames` -nyckeln hanteras korrekt.

<u>Faktiska resultat</u>:

Det finns en *500 undantag* i loggar, `GraphQLOperationNames` nyckeln hanteras inte korrekt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
