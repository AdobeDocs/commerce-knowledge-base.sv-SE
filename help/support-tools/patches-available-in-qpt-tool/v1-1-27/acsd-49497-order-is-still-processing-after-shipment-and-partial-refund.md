---
title: "ACSD-49497: Beställning som fortfarande bearbetas efter leverans och partiell återbetalning"
description: Använd patchen ACSD-49497 för att åtgärda Adobe Commerce-problemet där orderstatusen kvarstår som behandling efter leverans och en partiell återbetalning tillämpas.
exl-id: d195bcf4-bb8b-4373-8aad-a5b953b07443
feature: Admin Workspace, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-49497: Beställning som fortfarande bearbetas efter leverans och partiell återbetalning

Korrigeringsfilen ACSD-49497 åtgärdar ett problem där orderstatusen kvarstår som behandling efter leverans och en partiell återbetalning tillämpas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 är installerat. Korrigerings-ID är ACSD-49497. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Status för en ny order finns kvar i *[!UICONTROL Processing]* anges även efter leverans och en partiell återbetalning tillämpas.

<u>Steg som ska återskapas</u>:

1. Skapa en order med flera artiklar.
1. Från **[!UICONTROL Admin]** skapar du en faktura för ordern.
1. Från **[!UICONTROL Admin]**, skapa en kreditnota och återbetala en artikel endast delvis.
1. Från **[!UICONTROL Admin]** beställer du frakt för de återstående artiklarna i beställningen.
1. Observera orderstatus.

<u>Förväntade resultat</u>:

Orderns status ska vara *[!UICONTROL Complete]*.

<u>Faktiska resultat</u>:

Orderns status kvarstår *[!UICONTROL Processing]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
