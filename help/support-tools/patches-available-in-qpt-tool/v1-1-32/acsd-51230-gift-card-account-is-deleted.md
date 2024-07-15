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

Korrigeringen ACSD-51230 åtgärdar ett problem där presentkortskontot tas bort när den partiella återbetalningen av en enkel produkt bearbetas från en beställning. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.32 har installerats. Korrigerings-ID är ACSD-51230. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Presentkortskontot tas bort när en partiell återbetalning av en enkel produkt bearbetas från en order.

<u>Steg som ska återskapas</u>:

1. Skapa en beställning med ett *presentkort* och en *enkel produkt* (t.ex. *lägg till: SKU: GI000XX000XXX, SKU: PC046CP042076*) - (alla betalnings- och leveransmetoder fungerar).
1. Fakturera ordern.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Ett konto skapas för presentkortet.
1. Gå till **[!UICONTROL Order]** och skapa en **[!UICONTROL Credit Memo]**.
1. Ändra kvantiteten för *presentkortet* till 0 och uppdatera det. Detta skapar en partiell återbetalning för den *enkla produkten*.
1. Klicka på **[!UICONTROL Refund]**.
1. Uppdatera **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Det nyligen skapade kontot tas bort.

<u>Förväntade resultat</u>

Presentkortskontot kan användas eftersom återbetalningen inte skapades för presentkortet.

<u>Faktiska resultat</u>

Presentkortskontot tas bort och presentkortet återbetalas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
