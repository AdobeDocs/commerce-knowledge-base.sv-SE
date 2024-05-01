---
title: 'ACSD-47908: *Ett värde som är mindre än eller lika med 0 förväntas* fel vid utcheckning'
description: Använd patchen ACSD-47908 för att åtgärda Adobe Commerce-felet *Ett värde som är mindre än eller lika med 0 förväntas* när du väljer källa och kvantitet i leveranssteget under utcheckningen.
exl-id: fec90e4b-9cb8-4cd9-9e85-ccada840c896
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908: *Ett värde som är mindre än eller lika med 0 förväntas* fel vid utcheckning

Korrigeringen av ACSD-47908 åtgärdar felet *Ett värde som är mindre än eller lika med 0 förväntas* när du väljer källa och kvantitet i leveranssteget vid utcheckning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 är installerat. Korrigerings-ID är ACSD-47908. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Följande fel inträffar när källan och kvantiteten väljs i leveranssteget vid utcheckningen: *Ett värde som är mindre än eller lika med 0 förväntas*.

<u>Förutsättningar</u>:

Installera Adobe Commerce Inventory management-moduler (MSI).

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** och konfigurera flera källor.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** och skapa en ny stock.
   * Tilldela nu källorna till den nya stammen.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** och redigera minst en produkt.
   * Kontrollera att produkterna har tilldelats de nya källorna och ange tillgänglig kvantitet.
1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Orders]** och skapa en ny order.
1. Lägg till produkterna i beställningen och montera dem.
1. Klicka på **[!UICONTROL Ship]**.
1. Välj den källa som ska skickas från.
1. Ange kvantiteten för varje artikel som ska skickas.
1. Läs in sidan igen.
1. Klicka på **[!UICONTROL Proceed to Shipment]**.

<u>Förväntade resultat</u>:

Den nya utleveranssidan öppnas utan fel.

<u>Faktiska resultat</u>:

* Angiven kvantitet kan inte valideras.
* Följande fel genereras: *Ange ett värde mindre än eller lika med 0*.

  Felet är dock inkonsekvent och kanske inte alltid visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
