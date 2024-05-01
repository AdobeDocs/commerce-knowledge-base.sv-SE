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

# ACSD-54324: GraphQL `requisition_lists` begäran tar inte hänsyn till sidnumreringsinställningar

Korrigeringen ACSD-54324 åtgärdar ett problem där GraphQL `requisition_lists` begäran tar inte hänsyn till sidnumreringsinställningar och returnerar alla resultat. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.41 är installerat. Korrigerings-ID är ACSD-54324. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL `requisition_lists` begäran tar inte hänsyn till sidnumreringsinställningar och returnerar alla resultat.

<u>Steg som ska återskapas</u>:

1. Logga in på admin och navigera till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Ange *[!UICONTROL Enable Requisition List]* till *Ja*.

1. Logga in på frontend och gå till **[!UICONTROL My Requisition Lists]** från den översta menyn eller från **[!UICONTROL My Account]** och skapa flera rekvisitioner (exempel: 7).
1. När du har genererat en kundtoken kör du GraphQL nedan `requisition_lists` fråga efter kunden.

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

1. Observera att värdet för `total_count` fält 7, när det ska vara 4.

   Antalet objekt visar också 7 när det ska vara samma som *sidstorlek*.

<u>Förväntade resultat</u>:

* Numret visas som *sidstorlek* returneras under `total_count` och inte det totala antalet poster.
* Antalet objekt är detsamma som *sidstorlek*.

<u>Faktiska resultat</u>:

Det totala antalet poster returneras under `total_count`, även om *sidstorlek* omnämns.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
