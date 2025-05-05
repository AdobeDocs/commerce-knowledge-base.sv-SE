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

Korrigeringen ACSD-48362 åtgärdar ett problem där standardleveransadressen används istället för den nya adressen när en order läggs med en överlåtbar offert. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 har installerats. Korrigerings-ID är ACSD-48362. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Standardleveransadressen används i stället för den nyligen tillagda leveransadressen när en order läggs med en överlåtbar offert.

<u>Steg som ska återskapas</u>:

1. Aktivera B2B-citat genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. Logga in som företagsanvändare.
1. Lägg en produkt i kundvagnen.
1. Gå till kundvagnssidan och begär en offert.
1. Gå till kundens **[!UICONTROL My Quotes]**-sida och välj den offert som just skapades.
1. Gå till avsnittet **[!UICONTROL Shipping Information]** på kundens offertsida.
   * Klicka på **[!UICONTROL Add New Address]**, fyll i formuläret och spara adressen (markera inte **[!UICONTROL Use as my default billing address]** eller **[!UICONTROL Use as my default shipping address]**).
1. Klicka på **[!UICONTROL Send for Review]** på kundens offertsida.
1. Gå till Adobe Commerce Admin som administratör, öppna offerten som just har skapats och klicka på **[!UICONTROL Send]**.
1. Gå nu till kundens offertsida, uppdatera sidan och klicka på **[!UICONTROL Proceed to Checkout]**.
1. På utcheckningssidan visar data standardleveransadressen även när den nya leveransadressen har valts.
1. Klicka på **[!UICONTROL Continue]** och placera ordningen.

<u>Förväntade resultat</u>:

Ordern ska använda den nya adressen utan att välja standardleveransadressen på utcheckningssidan.

<u>Faktiska resultat</u>:

Ordern placeras med standardleveransadressen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur. 

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
