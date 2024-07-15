---
title: 'ACSD-56246: Schemaläggning av produktuppdateringar rensar flervalsattributvärden'
description: Använd korrigeringsfilen ACSD-56246 för att åtgärda Adobe Commerce-problemet där produktuppdateringar rensar flervalsattributvärden.
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: ddca8ac0-6aa8-4bf1-b8c2-4819758cb198
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56246: Produktuppdateringar som schemaläggs rensar flervalsattributvärden

Korrigeringen ACSD-56246 åtgärdar ett problem där schemaläggning av produktuppdateringar rensar värden för flera valda attribut. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 har installerats. Korrigerings-ID är ACSD-56246. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den schemalagda produkten uppdaterar flera attributvärden.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** och skapa följande attribut:

   * Standardetikett: Program
   * Katalogindatatyp för butiksägare: Flera val
   * Hantera alternativ (värden för ditt attribut): Choice, Sunscape, Safetyskärm
   * Attributkod: customer_program
   * Omfång: Global
   * Alternativ för Lägg till i kolumn: Nej
   * Använd i filteralternativ: Nej
   * Egenskaper för Storefront
   * Position: *333*
   * Tillåt HTML-taggar i Storefront: Nej

1. Kör
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Kör
   `bin/magento setup:upgrade`.
1. Gå till **[!UICONTROL Admin]** > Välj en enkel produkt > Markera alla objekt i programattributet > Klicka på **[!UICONTROL Save the product]**.
1. Schemalägg en uppdatering för den här produkten inom en minut och kör kommandot nedan för att få Content Staging att fungera:
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>Förväntade resultat</u>:

Produktens **[!UICONTROL program]**-attribut bör inte ändras.

<u>Faktiska resultat</u>:

Produktens **[!UICONTROL program]**-attribut har rensats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
