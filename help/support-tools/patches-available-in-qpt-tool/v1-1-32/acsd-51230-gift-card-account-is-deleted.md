---
title: 'ACSD-51230: Presentkortskontot har tagits bort'
description: Använd patchen ACSD-51230 för att åtgärda Adobe Commerce-problemet där presentkortskontot tas bort när den partiella återbetalningen av en enkel produkt bearbetas från en beställning.
exl-id: 4322a175-3641-468a-8a0f-fcbad90c758f
feature: Customer Service, Gift, Marketing Tools
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-51230: Presentkortskontot har tagits bort

Korrigeringen ACSD-51230 åtgärdar ett problem där presentkortskontot tas bort när den partiella återbetalningen av en enkel produkt bearbetas från en beställning. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.32 är installerat. Korrigerings-ID är ACSD-51230. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Presentkortskontot tas bort när en partiell återbetalning av en enkel produkt bearbetas från en order.

<u>Steg som ska återskapas</u>:

1. Skapa en order med en *Presentkort* och *enkel produkt* (till exempel *add: SKU: GI000XX000XXX, SKU: PC046CP042076*) - (alla betalnings- och leveransmetoder fungerar).
1. Fakturera ordern.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Ett konto skapas för presentkortet.
1. Gå till **[!UICONTROL Order]** och skapa **[!UICONTROL Credit Memo]**.
1. Ändra kvantiteten för *Presentkort* till 0 och uppdatera den. Detta skapar en partiell återbetalning för *enkel produkt*.
1. Klicka på **[!UICONTROL Refund]**.
1. Uppdatera nu **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Det nyligen skapade kontot tas bort.

<u>Förväntade resultat</u>

Presentkortskontot kan användas eftersom återbetalningen inte skapades för presentkortet.

<u>Faktiska resultat</u>

Presentkortskontot tas bort och presentkortet återbetalas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
