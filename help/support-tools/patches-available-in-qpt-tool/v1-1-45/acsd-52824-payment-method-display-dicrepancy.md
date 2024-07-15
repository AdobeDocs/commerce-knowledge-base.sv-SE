---
title: 'ACSD-52824: Inaktiverade betalningsmetoder som visas för företagskunder'
description: Använd korrigeringen ACSD-52824 för att åtgärda Adobe Commerce-problemet där  [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] betalningsmetoder visas för företagskunder trots att de är inaktiverade i företagsinställningarna.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 03496fb1-d492-4f02-9cdc-466cb571a2eb
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52824: Inaktiverade betalningsmetoder visas för företagskunder

Korrigeringen ACSD-52824 åtgärdar ett problem där betalningsmetoderna [!DNL PayPal Express], [!DNL Google Pay] och [!DNL Apple Pay] visas för företagskunder trots att de är inaktiverade i företagsinställningarna. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 har installerats. Korrigerings-ID är ACSD-52824. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Inaktiverade betalningsmetoder visas för företagskunder.

<u>Steg som ska återskapas</u>:

1. Konfigurera och aktivera [!DNL PayPal Express Checkout]. Navigera till **[!UICONTROL Basic Settings]** > markera **[!DNL PayPal Express Checkout]** och ange alternativet för **[!UICONTROL Display on Shopping Cart]** till *Ja*.
1. Konfigurera [!DNL Braintree] och aktivera [!DNL Apple Pay] och [!DNL Google Pay] till [!DNL Braintree].
1. Navigera till **[!UICONTROL Customers]** > **[!UICONTROL Companies]** och skapa ett nytt företag.
1. Klicka på **[!UICONTROL Advanced Settings]**, leta upp **[!UICONTROL Applicable Payment Methods]** och välj **[!UICONTROL Selected Payment Methods]**.
1. Under **[!UICONTROL Selected Payment Methods]** väljer du betalningsmetoder som är aktiverade och inte är associerade med *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]* eller *[!DNL Google Pay]*. Välj till exempel **[!UICONTROL Check/Money Order]**.
1. När du har valt lämpliga betalningsmetoder skapar du en ny kund och associerar den med det tidigare skapade företaget.
1. Logga in med det kundkonto som är associerat med företaget och fortsätt att lägga till artiklar i kundvagnen.
1. Var uppmärksam på minivagnen, kundvagnen och betalningssteget under utcheckningsprocessen.

<u>Förväntade resultat</u>:

Betalningsalternativen från [!DNL PayPal] och [!DNL Braintree] visas inte i minikorgen och kundvagnen.

<u>Faktiska resultat</u>:

Betalningsalternativen från [!DNL PayPal] och [!DNL Braintree] är fortfarande synliga i minikorgen och kundvagnen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
