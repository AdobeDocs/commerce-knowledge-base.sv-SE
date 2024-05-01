---
title: 'ACSD-47027: långsam fråga B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update'
description: Använd patchen ACSD-47027 för att åtgärda Adobe Commerce-problemet där B2B-frågan är långsam [!UICONTROL CompanyRole] [!DNL GraphQL] uppdatera.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027: långsam fråga B2B [!UICONTROL CompanyRole] [!DNL GraphQL] uppdatera

Korrigeringen ACSD-47027 löser problemet där den långsamma frågan B2B [!UICONTROL CompanyRole] [!DNL GraphQL] uppdateringen fungerar inte som förväntat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 är installerat. Korrigerings-ID är ACSD-47027. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**
* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den långsamma frågan B2B [!UICONTROL CompanyRole] [!DNL GraphQL] uppdateringen fungerar inte som förväntat.

<u>Förutsättningar</u>:

Installera B2B-modulen.

<u>Steg som ska återskapas</u>:

1. Gå till Adobe Commerce Admin **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** och ange **[!UICONTROL Enable Company]** till _Ja_.
1. Gå till fronten och skapa ett företag.
1. När du har loggat in som företagsanvändare går du till **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** och lägga till en ny roll.
1. Aktivera [!UICONTROL dev] frågelogg med `bin/magento dev:que:enab`.
1. Skicka nu nedanstående [!DNL GraphQL] request (id is the [!UICONTROL base64] kodat roll-ID):

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. Kontrollera frågeloggen.
1. Du ser att frågan ovan körs. Den här frågan körs i `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Förväntade resultat</u>:

The `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` måste optimeras för att undvika att läsa in alla data som finns i **[!UICONTROL company_permissions]** Databastabell.

<u>Faktiska resultat</u>:

Adobe Commerce kör en fråga utan något filter. När det finns ett stort antal poster tar det lång tid för Adobe Commerce att förbereda datainsamlingen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare. 

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
