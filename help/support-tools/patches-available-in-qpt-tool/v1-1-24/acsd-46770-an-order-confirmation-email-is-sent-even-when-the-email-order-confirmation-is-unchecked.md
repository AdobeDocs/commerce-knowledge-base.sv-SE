---
title: 'ACSD-46770: E-postmeddelande med orderbekräftelse skickas även när [!UICONTROL Email Order Confirmation] inte är markerat'
description: Använd patchen ACSD-46770 för att åtgärda Adobe Commerce-problemet där e-postmeddelanden med orderbekräftelse skickas även när [!UICONTROL Email Order Confirmation] inte har valts.
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770: E-postmeddelande med orderbekräftelse skickas även när **[!UICONTROL Email Order Confirmation]** inte är markerat

Korrigeringen ACSD-46770 åtgärdar ett problem där beställningar kan göras via REST API som gästanvändare även när **[!UICONTROL Email Order Confirmation]** inte är markerat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 har installerats. Korrigerings-ID är ACSD-46770. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett e-postmeddelande med orderbekräftelse skickas även när **[!UICONTROL Email Order Confirmation]** inte har valts.

<u>Steg som ska återskapas</u>:

1. Skapa ett kundkonto.
1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Order]** och klicka på **[!UICONTROL Create New Order]**.
1. Välj kund, lägg till produkterna i ordern, fyll i adressen och välj metoderna för leverans och betalning.
1. Avmarkera kryssrutan **[!UICONTROL Email Order confirmation]** innan du skickar ordern.
1. Klicka på **[!UICONTROL Submit Order]** för att skapa ordern.

<u>Förväntade resultat</u>:

Ett e-postmeddelande med orderbekräftelse ska inte skickas om **[!UICONTROL Email Order Confirmation]** inte är markerat.

<u>Faktiska resultat</u>:

Ett e-postmeddelande med orderbekräftelse skickas oavsett den omarkerade kryssrutan **[!UICONTROL Email Order Confirmation]**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
