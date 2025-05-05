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

Korrigeringen ACSD-54264 åtgärdar ett problem där felmeddelandet *Du kan inte uppdatera det begärda attributet. Rad-ID: store_id* visas när en kund försöker checka ut med en överlåtbar offert från en annan butiksvy. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 har installerats. Korrigerings-ID är ACSD-54264. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

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
1. Som administratör går du till **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** och skickar den godkända offerten.
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

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
