---
title: 'ACSD-54342: Felmeddelande vid import av CSV-fil utan giltiga data'
description: Åtgärda Adobe Commerce-problemet med korrigeringen ACSD-54342 där ett felaktigt felmeddelande visas när en CSV-fil importeras utan giltiga data.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 7f443ad8-c4b7-4294-b38f-9861e221bef2
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-54342: Felmeddelande vid import av CSV-fil utan giltiga data

Korrigeringen ACSD-54342 åtgärdar ett problem där ett felaktigt felmeddelande inträffar när en CSV-fil importeras utan giltiga data. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.39 är installerat. Korrigerings-ID är ACSD-54342. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett felaktigt felmeddelande visas när en CSV-fil importeras utan giltiga data.

<u>Steg som ska återskapas</u>:

1. Skapa en importfil med endast ogiltiga data (Exempel: [!DNL SKUs] som inte finns, ogiltiga kundadressfält eller felformaterade e-postadresser).
1. Importera filen och välj om du vill hoppa över valideringsfelen.

<u>Förväntade resultat</u>:

Valideringen misslyckas med `There are no valid rows to import` meddelande.

<u>Faktiska resultat</u>:

Valideringen godkänns, men importen misslyckas med `Error in data structure: values are mixed` meddelande.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
