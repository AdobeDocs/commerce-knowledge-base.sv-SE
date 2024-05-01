---
title: 'ACSD-48362: Standardleveransadressen används i stället för en ny.'
description: Använd patchen ACSD-48362 för att åtgärda Adobe Commerce-problemet där standardleveransadressen används i stället för en ny när en order läggs med en överlåtbar offert.
exl-id: 52f518b6-6f73-42cc-ac1b-c893cd5007fa
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-48362: Standardleveransadressen används i stället för en ny

Korrigeringen ACSD-48362 åtgärdar ett problem där standardleveransadressen används istället för den nya adressen när en order läggs med en överlåtbar offert. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 är installerat. Korrigerings-ID är ACSD-48362. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Standardleveransadressen används i stället för den nyligen tillagda leveransadressen när en order läggs med en överlåtbar offert.

<u>Steg som ska återskapas</u>:

1. Aktivera B2B-offert genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. Logga in som företagsanvändare.
1. Lägg en produkt i kundvagnen.
1. Gå till kundvagnssidan och begär en offert.
1. Gå till kundens **[!UICONTROL My Quotes]** och välj den offert som just skapades.
1. Gå till **[!UICONTROL Shipping Information]** på kundens offertsida.
   * Klicka **[!UICONTROL Add New Address]** fylla i formuläret och spara adressen (markera inte **[!UICONTROL Use as my default billing address]** eller **[!UICONTROL Use as my default shipping address]**).
1. Klicka **[!UICONTROL Send for Review]** på kundens offertsida.
1. Gå till Adobe Commerce Admin som administratör, öppna offerten som skapades och klicka på **[!UICONTROL Send]**.
1. Gå nu till kundens offertsida, uppdatera sidan och klicka på **[!UICONTROL Proceed to Checkout]**.
1. På utcheckningssidan visar data standardleveransadressen även när den nya leveransadressen har valts.
1. Klicka **[!UICONTROL Continue]** och lägga ordern.

<u>Förväntade resultat</u>:

Ordern ska använda den nya adressen utan att välja standardleveransadressen på utcheckningssidan.

<u>Faktiska resultat</u>:

Ordern placeras med standardleveransadressen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur. 

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
