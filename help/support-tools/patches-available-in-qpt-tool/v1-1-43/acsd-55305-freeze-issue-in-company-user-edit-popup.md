---
title: 'ACSD-55305: Popup fryser under redigering av företagsanvändare i [!UICONTROL My Account]'
description: Åtgärda Adobe Commerce-problemet med korrigeringen ACSD-55305 där [!UICONTROL Edit Company User] popup på [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] sidan fryser med en inläsare på skärmen.
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305: Popup fryser under redigering av företagsanvändare i [!UICONTROL My Account]

Korrigeringen ACSD-55305 åtgärdar ett problem där  [!UICONTROL Edit Company User] popup på [!UICONTROL My Account]> [!UICONTROL Company Structure] sidan fryser med en inläsare på skärmen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 är installerat. Korrigerings-ID är ACSD-55305. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel inträffar när du försöker använda *[!UICONTROL Edit Company User]* popup på *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* sida när den fryser när en inläsare visas på skärmen.

<u>Steg som ska återskapas</u>:

1. Skapa ett B2B-företag.
1. Skapa ett flervalsattribut för kunder.
1. Tilldela ett värde till det nya attributet för företagsadministratören.
1. Logga in som företagsadministratör.
1. Gå till [!UICONTROL account dashboard] och navigera till **[!UICONTROL Company Structure]**.
1. Markera användaren.
1. Klicka på **[!UICONTROL Edit Selected]**.

<u>Förväntade resultat</u>:

Formulärets popup-fönster visas korrekt, med möjlighet att redigera företagsinformation.

<u>Faktiska resultat</u>:

Formulärets popup-fönster visas utan möjlighet att redigera.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
