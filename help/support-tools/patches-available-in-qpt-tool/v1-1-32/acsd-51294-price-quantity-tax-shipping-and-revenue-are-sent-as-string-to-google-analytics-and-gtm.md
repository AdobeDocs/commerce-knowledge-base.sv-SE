---
title: '''ACSD-51294: Pris, kvantitet, moms, frakt, intäkt skickad som sträng till [!DNL Google Analytics] och GTM'
description: Använd patchen ACSD-51294 för att åtgärda Adobe Commerce-problemet där pris, kvantitet, moms, frakt och intäkter skickas som en sträng till [!DNL Google Analytics] och GTM.
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 159e1e98-0def-4b20-901d-f5f58c3ead7c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51294: Pris, kvantitet, moms, frakt, intäkt skickad som sträng till [!DNL Google Analytics] och GTM

Korrigeringen ACSD-51294 åtgärdar ett problem där pris, kvantitet, moms, frakt och intäkter skickas som en sträng till [!DNL Google Analytics] och GTM. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.32 är installerat. Korrigerings-ID är ACSD-51294. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Pris, kvantitet, moms, frakt och intäkter skickas som en sträng till [!DNL Google Analytics] och GTM.

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL Google Tag Manager] genom att navigera till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**.
2. Skapa en enkel produkt.
3. Slutför utcheckningen med den produkten.
4. Kontrollera `dataLayer` JavaScript-variabeln på sidan där utcheckningen lyckades.

<u>Förväntade resultat</u>

Pris- och kvantitetsvärden är numeriska.

<u>Faktiska resultat</u>

Pris- och kvantitetsvärden är strängar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool] guide.
