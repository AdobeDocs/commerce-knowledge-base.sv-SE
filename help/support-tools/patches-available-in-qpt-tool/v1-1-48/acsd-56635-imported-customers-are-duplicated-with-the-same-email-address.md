---
title: 'ACSD-56635: Importerade kunder dupliceras när kontodelning är inställd på [!DNL Global]'
description: Använd patchen ACSD-56635 för att åtgärda Adobe Commerce-problemet där den importerade kunden dupliceras med samma e-postadress när importen används med kontodelning inställd på [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
source-git-commit: 86d752c9c2791ef19960876afafe24fefe5d29ed
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635: Importerade kunder dupliceras med samma e-postadress när kontodelning är inställd på [!DNL Global]

Korrigeringen ACSD-56635 åtgärdar ett problem där den importerade kunden dupliceras med samma e-postadress när importen används med kontodelning inställd på [!DNL Global]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 är installerat. Korrigerings-ID är ACSD-56635. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Importerade kunder dupliceras med samma e-postadress när kontodelning är inställd på [!DNL Global].

<u>Steg som ska återskapas</u>:

1. Under Adobe Commerce (2.4-develop b2b) **[!UICONTROL Admin]**, åtkomst **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. Ange *[!UICONTROL Share Customer Accounts]* ange till *[!DNL Global]*.
1. Skapa flera webbplatser och butiker:

   * ws1 > s11, s12 > sw11, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Skapa en ny kund under *huvudwebbplats* från administratör med e-postadress som används som <adb@yormail.com>.
1. Under **[!UICONTROL Admin]**, navigera till **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. Välj **[!UICONTROL Customer Entity Type]** as *[!UICONTROL Customers Main File]*.
1. Använd samma e-postadress som <adb@yormail.com> på en annan webbplats, till exempel ws1. Se exemplet på CSV-filen customer.csv nedan.
1. Slutför importen för att se den nya användaren som skapades under *ws1* webbplats med samma e-postadress.

customer.csv-innehåll:

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>Förväntade resultat</u>:

Den importerade kunden med samma e-postadress uppdateras i stället för att dupliceras.

<u>Faktiska resultat</u>:

Duplicerade kunder skapas med samma e-postadress när kundimporten används.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
