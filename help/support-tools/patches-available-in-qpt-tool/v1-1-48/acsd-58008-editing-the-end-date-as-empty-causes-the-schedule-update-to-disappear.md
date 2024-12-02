---
title: 'ACSD-58008: Om du redigerar slutdatumet som *tom* försvinner schemauppdateringen'
description: Använd patchen ACSD-58008 för att åtgärda Adobe Commerce-problemet där redigering av slutdatumet som *tom* gör att schemauppdateringen försvinner.
feature: Staging, Page Content
role: Admin, Developer
exl-id: bfa590b8-377b-49dd-9aff-f89b8fd815c4
source-git-commit: d7ace1f20defb01105d4a241f971b06fca052215
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008: Om du redigerar slutdatumet som *tom* försvinner schemauppdateringen

ACSD-58008-korrigeringen åtgärdar ett problem där redigering av slutdatumet som *tom* gör att schemauppdateringen försvinner. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 har installerats. Korrigerings-ID är ACSD-58008. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du redigerar slutdatumet som *tom* försvinner schemauppdateringen

<u>Steg som ska återskapas</u>:

1. Logga in som [!UICONTROL Admin].
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** och skapa en sida.
1. Markera den skapade sidan och klicka på **[!UICONTROL Schedule New Update]**. *(Navigera det längst upp till höger på sidan)*.
1. Skapa fyra uppdateringar. *(t.ex. som en ökning på* 2 *minuter)*.
1. Uppdatera *uppdateringen* *och ändra tiden till en tidpunkt som ligger före den senaste uppdateringen*.
1. Spara uppdateringarna.

<u>Förväntade resultat</u>:

I schemauppdateringen visas *uppdateringen 3*.

<u>Faktiska resultat</u>:

Schemauppdateringen visar inte *uppdateringen 3*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
