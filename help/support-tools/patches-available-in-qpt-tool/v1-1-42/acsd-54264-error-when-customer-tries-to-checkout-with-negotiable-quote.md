---
title: 'ACSD-54264: Fel när kunden försöker checka ut med överlåtbar offert'
description: Åtgärda Adobe Commerce-problemet med korrigeringen ACSD-54264 där felmeddelandet"Du kan inte uppdatera det begärda attributet" visas. Rad-ID:store_id" visas när en kund försöker checka ut med en överlåtbar offert från en annan butiksvy.
feature: B2B, Checkout
role: Admin, Developer
exl-id: de8f451e-3b0a-4721-9ff4-18553477db1d
source-git-commit: 2e344b1ca4bc075bdbc9074bb431a398f0871698
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-54264: Fel uppstår när kunden försöker checka ut med överlåtbar offert

Korrigeringen ACSD-54264 åtgärdar ett problem där ett felmeddelande visas *Du kan inte uppdatera det begärda attributet. Rad-ID: store_id* visas när en kund försöker checka ut med en överlåtbar offert från en annan butiksvy. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 är installerat. Korrigerings-ID är ACSD-54264. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett felmeddelande *Du kan inte uppdatera det begärda attributet. Rad-ID: store_id* visas när en kund försöker checka ut med en överlåtbar offert från en annan butiksvy.

<u>Förutsättningar</u>:

Adobe Commerce B2B-moduler är installerade och aktiverade.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en butiksvy för standardwebbplatsen.
1. Aktivera *[!UICONTROL B2B Quote]* i konfigurationen.
1. Logga in som företagskund i någon av butiksvyerna.
1. Lägg till en produkt i *[!UICONTROL Shopping Cart]*.
1. Skicka offerten för granskning.
1. Som administratör går du till **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** och skicka den godkända offerten.
1. Som företagskund ändrar du butiksvyn till en annan butiksvy.
1. Försök checka ut.

<u>Förväntade resultat</u>:

Kunden lägger en order med denna offert.

<u>Faktiska resultat</u>:

* Felet inträffar när leveransinformationen sparas:

  `You cannot update the request attribute. Row ID: store_id =#`

* Följande fel loggas:

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
