---
title: 'ACSD-49822: Uppdateringar på rekvisitionslistsidan återspeglas inte i utskriftsrekvisitionslistan'
description: Använd patchen ACSD-49822 för att åtgärda Adobe Commerce-problemet där uppdateringarna på rekvisitionslistsidan inte visas i listan över utskriftsrekvisitioner.
exl-id: 584e3fcd-9153-41aa-8857-cf1fa41269c9
feature: Admin Workspace, B2B
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-49822: Uppdateringar i rekvisitionslistan återspeglas inte i utskriftsrekvisitionslistan

Korrigeringen ACSD-49822 åtgärdar ett problem där uppdateringar på rekvisitionslistsidan inte visas i listan över utskriftsrekvisitioner. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 är installerat. Korrigerings-ID är ACSD-49822. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Uppdateringar på rekvisitionslistsidan återspeglas inte i utskriftsrekvisitionslistan.

<u>Steg som ska återskapas</u>:

1. Aktivera rekvisitionslistan genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[B2B-funktioner]**.
1. Skapa en produkt.
1. Logga in som kund och lägg till två produkter i rekvisitionslistan.
1. Gå till **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. Visa en rekvisitionslista.
1. Klicka **[!UICONTROL Print]** i det övre högra hörnet.
1. Stäng utskriftsfönstret och listsidan för utskriftsrekvisitioner.
1. Ta bort en artikel i listan eller uppdatera en kvantitet av en artikel och försök skriva ut den igen.
1. Observera att objekten inte uppdateras i utskriftsfönstret.
1. Stäng utskriftsfönstret.
1. Observera att objekten inte uppdateras på sidan för utskrift av rekvisitionslista.

<u>Förväntade resultat</u>:

Listan som ska skrivas ut uppdateras när ändringarna har tillämpats.

<u>Faktiska resultat</u>:

Uppdateringar visas inte på sidan för utskrift av rekvisitionslista.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
