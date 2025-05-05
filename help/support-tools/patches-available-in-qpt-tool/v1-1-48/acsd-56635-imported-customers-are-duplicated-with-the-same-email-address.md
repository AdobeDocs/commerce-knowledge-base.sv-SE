---
title: 'ACSD-56635: Importerade kunder dupliceras när kontodelning är inställd på  [!DNL Global]'
description: Använd korrigeringsfilen ACSD-56635 för att åtgärda Adobe Commerce-problemet där den importerade kunden dupliceras med samma e-postadress när importen används med kontodelning inställd på  [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
exl-id: abd542a1-6764-4385-97a6-b46015363b42
source-git-commit: 880fc679afc853b514fddda56e570fe1a279a3d9
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635: Importerade kunder dupliceras med samma e-postadress när kontodelning har angetts till [!DNL Global]

Korrigeringen ACSD-56635 åtgärdar ett problem där den importerade kunden dupliceras med samma e-postadress när importen används med kontodelning inställd på [!DNL Global]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 har installerats. Korrigerings-ID är ACSD-56635. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Importerade kunder dupliceras med samma e-postadress när kontodelning är inställd på [!DNL Global].

<u>Steg som ska återskapas</u>:

1. Under Adobe Commerce (2.4-develop b2b) **[!UICONTROL Admin]**, gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. Ange inställningen *[!UICONTROL Share Customer Accounts]* till *[!DNL Global]*.
1. Skapa flera webbplatser och butiker:

   * ws1 > s11, s12 > sw11, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Skapa en ny kund på *huvudwebbplatsen* från en administratör med en e-postadress som används som <adb@yormail.com>.
1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Import]** under **[!UICONTROL Admin]**.
1. Välj **[!UICONTROL Customer Entity Type]** som *[!UICONTROL Customers Main File]*.
1. Använd samma e-postadress som <adb@yormail.com> på en annan webbplats, till exempel Windows1. Se exemplet på CSV-filen customer.csv nedan.
1. Slutför importen för att se den nya användaren som skapades på webbplatsen *ws1* med samma e-postadress.

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

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
