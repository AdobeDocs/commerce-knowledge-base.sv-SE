---
title: 'ACSD-54324: Begäran från GraphQL rekvisisition_lists tar inte hänsyn till sidnumreringsinställningar'
description: Använd ACSD-54324-korrigeringen för att åtgärda Adobe Commerce-problemet där GraphQL-begäran "reksition_lists" inte tar hänsyn till sidnumreringsinställningar och returnerar alla resultat.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324: Sidnumreringsinställningar tas inte med i GraphQL `requisition_lists`-begäran.

Korrigeringen ACSD-54324 åtgärdar ett problem där GraphQL `requisition_lists`-begäran inte tar hänsyn till sidnumreringsinställningar och returnerar alla resultat. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.41 har installerats. Korrigerings-ID är ACSD-54324. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL `requisition_lists`-begäran tar inte hänsyn till sidnumreringsinställningar och returnerar alla resultat.

<u>Steg som ska återskapas</u>:

1. Logga in som administratör och navigera till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Ange *[!UICONTROL Enable Requisition List]* som *Ja*.

1. Logga in på klientsidan och gå till **[!UICONTROL My Requisition Lists]** från den översta menyn eller från **[!UICONTROL My Account]** och skapa flera rekvisitioner (exempel: 7).
1. När du har genererat en kundtoken kör du GraphQL `requisition_lists`-frågan nedan för kunden.

   * Kontrollera att sidstorleken är mindre än det totala antalet rekvisitionslistor som du har skapat (exempel: 4)

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. Observera att värdet för fältet `total_count` är 7, när det ska vara 4.

   Antalet objekt visar också 7 när det ska vara samma som *sidstorleken*.

<u>Förväntade resultat</u>:

* Numret som visas som *sidstorlek* returneras under `total_count` och inte under det totala antalet poster.
* Antalet objekt är samma som *sidstorleken*.

<u>Faktiska resultat</u>:

Det totala antalet poster returneras under `total_count`, även om *sidstorleken* nämns.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
