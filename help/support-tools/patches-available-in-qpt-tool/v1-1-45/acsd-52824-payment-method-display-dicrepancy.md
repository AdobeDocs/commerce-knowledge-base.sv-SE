---
title: 'ACSD-52824: Inaktiverade betalningsmetoder som visas för företagskunder'
description: Åtgärda Adobe Commerce-problemet med ACSD-52824 där [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] betalningsmetoder visas för företagskunder trots att de är inaktiverade i företagsinställningarna.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 03496fb1-d492-4f02-9cdc-466cb571a2eb
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52824: Inaktiverade betalningsmetoder visas för företagskunder

Korrigeringen ACSD-52824 åtgärdar ett problem där [!DNL PayPal Express], [!DNL Google Pay]och [!DNL Apple Pay] betalningsmetoder visas för företagskunder trots att de är inaktiverade i företagsinställningarna. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 är installerat. Korrigerings-ID är ACSD-52824. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Inaktiverade betalningsmetoder visas för företagskunder.

<u>Steg som ska återskapas</u>:

1. Konfigurera och aktivera [!DNL PayPal Express Checkout]. Navigera till **[!UICONTROL Basic Settings]** > markera **[!DNL PayPal Express Checkout]** och ange alternativ för **[!UICONTROL Display on Shopping Cart]** till *Ja*.
1. Konfigurera [!DNL Braintree] och aktivera [!DNL Apple Pay] och [!DNL Google Pay] via [!DNL Braintree].
1. Navigera till **[!UICONTROL Customers]** > **[!UICONTROL Companies]** och skapa ett nytt företag.
1. Klicka på **[!UICONTROL Advanced Settings]**, leta upp **[!UICONTROL Applicable Payment Methods]** och välja **[!UICONTROL Selected Payment Methods]**.
1. Under **[!UICONTROL Selected Payment Methods]** väljer du betalningsmetoder som är aktiverade och inte är kopplade till *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]*, eller *[!DNL Google Pay]*. Välj till exempel **[!UICONTROL Check/Money Order]**.
1. När du har valt lämpliga betalningsmetoder skapar du en ny kund och associerar den med det tidigare skapade företaget.
1. Logga in med det kundkonto som är associerat med företaget och fortsätt att lägga till artiklar i kundvagnen.
1. Var uppmärksam på minivagnen, kundvagnen och betalningssteget under utcheckningsprocessen.

<u>Förväntade resultat</u>:

Betalningsalternativ från [!DNL PayPal] och [!DNL Braintree] är inte synliga i minivagnen och shoppingvagnen.

<u>Faktiska resultat</u>:

Betalningsalternativ från [!DNL PayPal] och [!DNL Braintree] förbli synlig i minivagnen och shoppingvagnen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
