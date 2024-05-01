---
title: "ACSD-46581: Den beräknade momssumman uppdateras inte när du har valt ett land i kundvagnen"
description: Använd patchen ACSD-46581 för att lösa problemet med Adobe Commerce där momssatsen inte uppdateras efter att landet bytt i kundvagnen.
exl-id: 17334f7b-e5a2-4091-8196-eff80875c003
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-46581: Den beräknade momssumman uppdateras inte när du har valt ett land i kundvagnen

Denna ACSD-46581-korrigering löser problemet där skattesatsen inte uppdateras efter att landet bytt i kundvagnen. Den uppdateras först när du har valt leveranssätt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 är installerat. Korrigerings-ID är ACSD-46581. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
* Adobe Commerce (alla distributionsmetoder) 2.4.1-p1

**Kompatibel med Adobe Commerce:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Momssatsen uppdateras inte när landet har bytt i kundvagnen.

<u>Steg som ska återskapas</u>:

1. Gå till Adobe Commerce Admin **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. Skapa en ny momssats för **[!UICONTROL Country]** = _Amerikas förenta stater_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8,25_.
1. Skapa en ny momssats för **[!UICONTROL Country]** = _Indien_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Skapa en skatteregel med både skattesatser för USA och Indien.
1. Gå till **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** och aktivera fler än en fraktmetod (_Schablonbelopp_ och _Fri frakt_ till exempel).
1. Skapa en enkel produkt med **[!UICONTROL Taxable Goods]** momsklass.
1. Lägg produkten i varukorgen på butikens framsida.
1. Öppna kundvagnen och kontrollera momsbeloppet.
1. Standardskatteinställningarna för USA används och momsen beräknas baserat på en 8,25-procentig skattesats.
1. Byt land till Indien.

<u>Förväntade resultat</u>:

Skattebeloppet ändrades till 10 % när landet bytte till Indien.

<u>Faktiska resultat</u>:

Momsbeloppet är detsamma i kundvagnens totala avsnitt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
