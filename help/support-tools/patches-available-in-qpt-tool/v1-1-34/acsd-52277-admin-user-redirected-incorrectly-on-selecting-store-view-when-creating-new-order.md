---
title: "ACSD-52277: Administratörsanvändaren omdirigerades felaktigt när butiksvyn skulle väljas när en ny order skapades"
description: Använd patchen ACSD-52277 för att åtgärda Adobe Commerce-problemet där en administratörsanvändare inte omdirigeras korrekt efter att butiksvyn har valts när en ny order skapas i Admin.
exl-id: 6f0b86ae-f6f1-44cf-aef5-64def5f14824
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-52277: Administratörsanvändaren omdirigeras felaktigt när butiksvyn väljs när en ny order skapas

Korrigeringen ACSD-52277 åtgärdar ett problem där en administratörsanvändare inte omdirigeras korrekt efter att butiksvyn har valts när en ny order skapas i Admin. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 är installerat. Korrigerings-ID är ACSD-52277. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4, 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En administratörsanvändare omdirigeras inte korrekt efter att butiksvyn har valts när en ny order skapas.

<u>Steg som ska återskapas</u>

1. Installera en ren instans.
1. Skapa en produkt.
1. Skapa ytterligare en webbplats, en butik och två butiksvyer.
1. Skapa en beställning från administratören genom att välja *butiksvy 1*.

<u>Förväntade resultat</u>:

Användaren omdirigeras till ordersidan.

<u>Faktiska resultat</u>:

Användaren omdirigeras inte till ordersidan när butiksvyn har valts.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
