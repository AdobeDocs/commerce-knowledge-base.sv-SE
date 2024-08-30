---
title: 'ACSD-58446: Om du tar bort ett team med underordnade användare eller team via GraphQL visas ett felmeddelande utan information '
description: Använd ACSD-58446-korrigeringen för att åtgärda Adobe Commerce-problemet där ett team med underordnade användare eller team via GraphQL returnerar ett felmeddelande som inte är informativt och som inte stämmer överens med användargränssnittet.
feature: Product, GraphQL, Company
role: Admin, Developer
source-git-commit: ab290f7c5b052aa220b3ef003febd9afc1cfdf00
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-58446: Om du tar bort ett team med underordnade användare eller team via GraphQL visas ett felmeddelande utan information

Korrigeringen ACSD-58446 åtgärdar ett problem med Adobe Commerce där ett team med underordnade användare eller team via GraphQL returnerar ett felmeddelande som inte är informativt och som inte stämmer överens med användargränssnittet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 har installerats. Korrigerings-ID är ACSD-58446. Observera att problemet är planerat att åtgärdas i Adobe Commerce B2B 1.5.1

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce och Magento Open Source:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du tar bort ett team med underordnade användare eller team via GraphQL visas ett felmeddelande som inte är informativt och som inte stämmer överens med användargränssnittet.

## Förhandsvillkor:

Installerade B2B-moduler.

<u>Steg som ska återskapas</u>:

1. Aktivera funktionen *[!UICONTROL Company]*.
1. Skapa ett nytt företag.
1. Logga in på **[!UICONTROL Admin]** och aktivera företagskontot.
1. Kontrollera e-postadressen och ange ett lösenord för det nya företagskontot.
1. Skapa ett nytt team för företaget.
1. Logga in som **[!UICONTROL company user]** på frontend och lägg till en **[!UICONTROL new user]** för det skapade teamet.
1. Logga in på **[!UICONTROL Admin]**, inaktivera företagsanvändaren och ange *[!UICONTROL Customer Active]* = *Nej*
1. Se till att ta bort det skapade teamet via GraphQL.

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>Förväntade resultat</u>:

Ett informativt felmeddelande som är konsekvent med användargränssnittet returneras.

<u>Faktiska resultat</u>:

Ett allmänt internt serverfelmeddelande returneras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
