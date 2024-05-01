---
title: 'ACSD-49502: Hämtningsbar länk har inte uppdaterats korrekt efter [!DNL staging] update'
description: Åtgärda Adobe Commerce-problemet med korrigeringen ACSD-49502 där den hämtningsbara länken inte uppdateras korrekt efter en [!DNL staging] uppdateringen tillämpas på den hämtningsbara produkten.
exl-id: 9e7f0c06-4b7d-42c4-8ec7-cdeefd7e8a08
feature: Staging
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-49502: Hämtningsbar länk har inte uppdaterats korrekt efter [!DNL staging] uppdatera

Korrigeringen ACSD-49502 åtgärdar ett problem där den hämtningsbara länken inte uppdateras korrekt efter en [!DNL staging] uppdateringen tillämpas på den hämtningsbara produkten. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 är installerat. Korrigerings-ID är ACSD-49502. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den hämtningsbara länken uppdateras inte korrekt efter en [!DNL staging] uppdateringen tillämpas på den hämtningsbara produkten.

<u>Steg som ska återskapas</u>:

1. Skapa en nedladdningsbar produkt med länkar.
1. Skapa ett kundkonto och logga in.
1. Lägg den nedladdningsbara produkten i kundvagnen från butiken.
1. I **[!UICONTROL Admin]**, schemalägg en ny uppdatering för den hämtningsbara produkten och låt den schemalagda uppdateringen slutföras.
1. Slutför beställningen i butiken.

<u>Förväntade resultat</u>:

Hämtningsbara länkar bevaras när schemalagda uppdateringar används medan tidigare tillagda produkter finns i kundvagnen.

<u>Faktiska resultat</u>:

Länkar som kan hämtas saknas både under kundens *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) och beställa vysidor i  **[!UICONTROL Admin]**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
