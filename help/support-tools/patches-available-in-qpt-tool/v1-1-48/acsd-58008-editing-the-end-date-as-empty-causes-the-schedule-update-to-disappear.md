---
title: 'ACSD-58008: Om du redigerar slutdatumet som *empty* försvinner schemauppdateringen.'
description: Använd patchen ACSD-58008 för att åtgärda Adobe Commerce-problemet där redigering av slutdatumet som *tom* gör att schemauppdateringen försvinner.
feature: Staging, Page Content
role: Admin, Developer
source-git-commit: 174ed3b35edeb26b09b04bc7d88111a5719e08f8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008: Redigerar slutdatumet som *tom* gör att schemauppdateringen försvinner

Korrigeringen ACSD-58008 åtgärdar ett problem där slutdatumet redigeras som *tom* gör att schemauppdateringen försvinner. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 är installerat. Korrigerings-ID är ACSD-58008. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Redigera slutdatumet som *tom* gör att schemauppdateringen försvinner

<u>Steg som ska återskapas</u>:

1. Logga in som [!UICONTROL Admin].
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** och skapa en sida.
1. Markera den skapade sidan och klicka på **[!UICONTROL Schedule New Update]**. *(Navigera till det övre högra hörnet på sidan)*.
1. Skapa fyra uppdateringar. *(t.ex. som en ökning av* 2 *minuter)*.
1. Uppdatera *uppdatering 2* och ändra tiden till en tidpunkt som ligger före den sista *uppdatering 4*.
1. Spara uppdateringarna.

<u>Förväntade resultat</u>:

Schemauppdateringen visar *uppdatering 3*.

<u>Faktiska resultat</u>:

Schemauppdateringen visar inte *uppdatering 3*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.