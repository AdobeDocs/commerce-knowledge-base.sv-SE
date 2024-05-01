---
title: 'ACSD-46770: e-postmeddelande med orderbekräftelse skickas även när [!UICONTROL Email Order Confirmation] är inte markerad'
description: Använd patchen ACSD-46770 för att åtgärda Adobe Commerce-problemet där e-postmeddelanden med orderbekräftelse skickas även när [!UICONTROL Email Order Confirmation] är inte markerat.
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770: e-postmeddelande med orderbekräftelse skickas även när **[!UICONTROL Email Order Confirmation]** är avmarkerad

Korrigeringen ACSD-46770 åtgärdar ett problem där beställningar kan göras via REST API som gästanvändare även när **[!UICONTROL Email Order Confirmation]** är omarkerad. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 är installerat. Korrigerings-ID är ACSD-46770. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett e-postmeddelande med en orderbekräftelse skickas även när **[!UICONTROL Email Order Confirmation]** är inte markerat.

<u>Steg som ska återskapas</u>:

1. Skapa ett kundkonto.
1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Order]** och klicka på  **[!UICONTROL Create New Order]**.
1. Välj kund, lägg till produkterna i ordern, fyll i adressen och välj metoderna för leverans och betalning.
1. Innan du skickar ordern avmarkerar du **[!UICONTROL Email Order confirmation]** kryssruta.
1. Klicka på **[!UICONTROL Submit Order]** för att skapa ordern.

<u>Förväntade resultat</u>:

Ett e-postmeddelande med orderbekräftelse ska inte skickas om **[!UICONTROL Email Order Confirmation]** är omarkerad.

<u>Faktiska resultat</u>:

Ett e-postmeddelande med orderbekräftelse skickas oavsett om det är omarkerat eller inte **[!UICONTROL Email Order Confirmation]** kryssruta.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
