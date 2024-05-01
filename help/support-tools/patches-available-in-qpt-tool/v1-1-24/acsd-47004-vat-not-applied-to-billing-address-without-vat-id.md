---
title: 'ACSD-47004: moms tillämpas inte på faktureringsadress utan moms-ID'
description: Använd patchen ACSD-47004 för att åtgärda Adobe Commerce-problemet där moms inte tillämpas på en faktureringsadress utan moms-ID.
exl-id: 04706219-be1d-4d9a-a8bf-f5c24b45076d
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---

# ACSD-47004: moms tillämpas inte på faktureringsadressen utan moms-ID

Korrigeringen ACSD-47004 åtgärdar ett problem där moms inte tillämpas på en faktureringsadress utan ett moms-ID. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)  1.1.24 är installerat. Korrigerings-ID är ACSD-47004. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

moms tillämpas inte på en faktureringsadress utan ett moms-ID.

<u>Steg som ska återskapas</u>:

1. Öppna [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** och ange **[!UICONTROL Enable Automatic Assignment to Customer Group]** till *[!UICONTROL Yes]*.
1. Ange olika grupper för moms-ID-valideringar. Exempel:
   ![VAT-ID-validations](/help/support-tools/patches-available-in-qpt-tool/assets/vat-id-validations.png)
1. Registrera en ny kund.
1. Lägg till en ny standardadress utan moms. Exempel:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Verifiera att kundens grupp kvarstår [!UICONTROL General].
1. Redigera den här adressen och lägg till ett giltigt momsregistreringsnummer:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Se till att kundens grupp har ändrats till [!UICONTROL Retailer].
1. Redigera adressen och ta bort momsregistreringsnumret:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>Förväntade resultat</u>:

Kundgruppen ändras till standardvärdet [!UICONTROL General] gruppera automatiskt.

<u>Faktiska resultat</u>:

Kundgruppen ändras inte till standardvärdet [!UICONTROL General] gruppera automatiskt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
