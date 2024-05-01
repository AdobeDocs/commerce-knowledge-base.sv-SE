---
title: 'ACSD-46617: **[!UICONTROL Continue to Checkout]**-knapp nedtonad när delsumman är större än det konfigurerade minimiorderbeloppet'
description: Använd patchen ACSD-46617 för att lösa Adobe Commerce-problemet där **[!UICONTROL Continue to Checkout]** är nedtonad även om delsumman är större än det konfigurerade minimiorderbeloppet.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617:[!UICONTROL Continue to Checkout]&quot;-knapp nedtonad när delsumman är större än &quot;[!UICONTROL Minimum Order Amount]&quot;

Denna ACSD-46617-korrigering löser problemet där **[!UICONTROL Continue to Checkout]** är nedtonad även om delsumman är större än det konfigurerade minimiorderbeloppet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 är installerat. Korrigerings-ID är ACSD-46617. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The **[!UICONTROL Continue to Checkout]** är nedtonad även om delsumman är större än det konfigurerade minimiorderbeloppet.

<u>Steg som ska återskapas</u>:

1. Gå till Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** och ange följande:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. Skapa en [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Skapa en produkt till priset av 25 USD.
1. Lägg produkten i kundvagnen.
1. Gå till kundvagnen och välj $5 **[!UICONTROL Flat Rate shipping]** och tillämpa kupongkoden.
1. Gå till kassan, slutför leveransen och navigera till **[!UICONTROL Paytment]** -avsnitt.
1. Gå tillbaka till kundvagnen.

<u>Förväntade resultat</u>:

Det finns inget fel relaterat till minimiorderbeloppet eftersom totalsumman på $2.4 är större än vad som krävs på $2.

<u>Faktiska resultat</u>:

* Det finns ett fel relaterat till minimiorderbeloppet även när totalsumman på $2.4 är större än minimiorderbeloppet på $2.
* The **[!UICONTROL Continue to Checkout]** knappen är nedtonad.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
