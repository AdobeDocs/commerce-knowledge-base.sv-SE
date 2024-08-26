---
title: 'ACSD-56979: Produktbilder som tagits bort efter att mellanlagringsuppdateringen tagits bort'
description: Använd korrigeringsfilen ACSD-56979 för att åtgärda Adobe Commerce-problemet där produktbilder tas bort efter att en mellanlagringsuppdatering har tagits bort
feature: Products
role: Admin, Developer
source-git-commit: 8e916feab8be9d92d047fae8861a479070d448e8
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-56979: Produktbilder som tagits bort efter att mellanlagringsuppdateringen tagits bort

Korrigeringen ACSD-56979 åtgärdar ett problem där produktbilder tas bort efter att en mellanlagringsuppdatering har tagits bort. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 har installerats. Korrigerings-ID är ACSD-56979. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce och Magento Open Source:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktbilder tas bort när en mellanlagringsuppdatering har tagits bort.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** på sidofältet för Commerce Admin och skapa en produkt.
1. Under **[!UICONTROL Images and Videos]** överför du en bild och sparar produkten.
1. Välj **[!UICONTROL Schedule New Update]** i rutan **[!UICONTROL Scheduled Changes]**.
   1. Välj ett startdatum några minuter i framtiden.
   1. Välj inget slutdatum.
1. Markera länken **[!UICONTROL View/Edit]** i rutan **[!UICONTROL Scheduled Changes]**.
1. Gå till **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]** och välj **[!UICONTROL Done]**.
1. Uppdatera sidan.

<u>Förväntade resultat</u>:

Eftersom uppdateringen tas bort före det schemalagda startdatumet bör produkten förbli densamma.

<u>Faktiska resultat</u>:

Bildinnehållet går förlorat och visar noll byte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
