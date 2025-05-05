---
title: 'ACSD-47027: långsam fråga B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update'
description: Använd korrigeringsfilen ACSD-47027 för att åtgärda Adobe Commerce-problemet där det finns en långsam uppdatering av B2B [!UICONTROL CompanyRole] [!DNL GraphQL] -frågan.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027: långsam fråga B2B [!UICONTROL CompanyRole] [!DNL GraphQL] uppdatering

Korrigeringen ACSD-47027 löser problemet där den långsamma uppdateringen av fråga B2B [!UICONTROL CompanyRole] [!DNL GraphQL] inte fungerar som förväntat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 har installerats. Korrigerings-ID är ACSD-47027. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den långsamma uppdateringen av fråga B2B [!UICONTROL CompanyRole] [!DNL GraphQL] fungerar inte som förväntat.

<u>Förutsättningar</u>:

Installera B2B-modulen.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** i Adobe Commerce Admin och ange **[!UICONTROL Enable Company]** som _Ja_.
1. Gå till fronten och skapa ett företag.
1. När du har loggat in som företagsanvändare går du till **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** och lägger till en ny roll.
1. Aktivera [!UICONTROL dev]-frågelogg med `bin/magento dev:que:enab`.
1. Skicka nu begäran [!DNL GraphQL] nedan (id är det [!UICONTROL base64]-kodade roll-ID:t):

   <pre><code>
   mutation &lbrace;
   updateCompanyRole(
      input: &lbrace;
         id: "Mg=="
         permissions: &lbrack;
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        &rbrack;
      &rbrace;
    ) &lbrace;
      role &lbrace;
         id

         name

         permissions &lbrace;
         id

         text

         children &lbrace;
            id

            text

            children &lbrace;
               id

               text
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
   </code></pre>

1. Kontrollera frågeloggen.
1. Du ser att frågan ovan körs. Frågan körs i `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Förväntade resultat</u>:

`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` måste optimeras för att undvika inläsning av alla data som är tillgängliga i databastabellen **[!UICONTROL company_permissions]**.

<u>Faktiska resultat</u>:

Adobe Commerce kör en fråga utan något filter. När det finns ett stort antal poster tar det lång tid för Adobe Commerce att förbereda datainsamlingen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation. 

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
