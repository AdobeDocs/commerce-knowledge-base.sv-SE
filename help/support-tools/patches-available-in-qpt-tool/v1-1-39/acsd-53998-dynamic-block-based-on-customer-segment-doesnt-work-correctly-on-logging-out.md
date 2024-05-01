---
title: 'ACSD-53998: Dynamiskt block som baseras på kundsegment fungerar felaktigt efter utloggning'
description: Använd patchen ACSD-53998 för att åtgärda Adobe Commerce-problemet där ett dynamiskt block som baseras på ett kundsegment inte fungerar korrekt efter utloggning från ett kundkonto.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
exl-id: 5a82a6b8-e8f7-47ff-89f6-93a39b72fe38
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-53998: Dynamiskt block som baseras på kundsegment fungerar felaktigt efter utloggning

Korrigeringen ACSD-53998 åtgärdar ett problem där ett dynamiskt block som baseras på ett kundsegment inte fungerar korrekt efter utloggning från ett kundkonto. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.39 är installerat. Korrigerings-ID är ACSD-53998. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett dynamiskt block som baseras på ett kundsegment fungerar inte korrekt efter utloggning från ett kundkonto.

<u>Förutsättningar</u>:

Installera och aktivera [!DNL Page Builder] moduler.

<u>Steg som ska återskapas</u>:

1. Skapa två kundsegment utan villkor.
1. Skapa två dynamiska block för varje segment.
1. Skapa ett block med de två dynamiska blocken som [!DNL Page Builder] dynamiska block.
1. Skapa en widget med det ovanstående blocket och gör blocket synligt under sidfotsavsnittet på alla sidor.
1. Rensa cacheminnen.
1. Öppna hemsidan.
1. Logga in som kund.
1. Logga ut.

<u>Förväntade resultat</u>:

Banderollen som skapats för inloggade kunder visas inte för gästanvändare.

<u>Faktiska resultat</u>:

Banderollen som skapats för det inloggade kundsegmentet visas även efter utloggning från kundkontot.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
