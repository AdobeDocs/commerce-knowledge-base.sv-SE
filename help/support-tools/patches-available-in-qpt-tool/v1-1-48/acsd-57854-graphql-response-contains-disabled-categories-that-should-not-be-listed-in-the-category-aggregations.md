---
title: 'ACSD-57854: *GraphQL*-svar innehåller inaktiverade kategorier som inte ska listas i kategoriaggregeringarna'
description: Använd korrigeringen ACSD-57854 för att åtgärda Adobe Commerce-problemet där *GraphQL*-svaret innehåller inaktiverade kategorier som inte ska listas i kategoriaggregeringarna.
feature: GraphQL
role: Admin, Developer
exl-id: b6130a0f-57bc-4719-99f2-beb630c463c7
source-git-commit: ea6f23a7ce599e24c6b683f82cf08b72b2506020
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57854: *GraphQL*-svar innehåller inaktiverade kategorier som inte ska listas i kategoriaggregeringar

Korrigeringen ACSD-57854 åtgärdar ett problem där svaret *GraphQL* innehåller inaktiverade kategorier som inte ska listas i kategoriaggregeringarna. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.48 har installerats. Patch-ID:t är ACSD-57854. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

*GraphQL*-svaret innehåller inaktiverade kategorier som inte ska listas i kategoriaggregeringarna.

<u>Steg som ska återskapas</u>:

1. Skapa två kategorier.
1. Skapa en produkt (Test Adobe Product) och tilldela produkten till båda kategorierna.
1. Inaktivera en av kategorierna som skapades.
1. Använd produkterna *GraphQL* för att söka efter produkten.
1. Kontrollera listan över produktkategorier i svaret på *GraphQL*.

<u>Förväntade resultat</u>:

De inaktiverade kategorierna visas inte i svaret *GraphQL*.

<u>Faktiska resultat</u>:

De inaktiverade kategorierna listas i kategoriaggregeringssvaret *GraphQL*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
