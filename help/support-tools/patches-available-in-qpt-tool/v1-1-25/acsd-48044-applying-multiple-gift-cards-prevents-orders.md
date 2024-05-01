---
title: 'ACSD-48044: Att använda flera presentkort förhindrar att beställningar görs'
description: Använd patchen ACSD-48044 för att åtgärda Adobe Commerce-problemet där det inte går att lägga in flera presentkort på en enda order med flera leveranser.
exl-id: fe57063c-d69c-4b80-a59c-912c2603f6af
feature: Admin Workspace, Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-48044: Användning av flera presentkort förhindrar att beställningar görs

Korrigeringen ACSD-48044 åtgärdar ett problem där det inte går att lägga order på flera presentkort på en enda order med flera leveranser. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 är installerat. Korrigerings-ID är ACSD-48044. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Att lägga på flera presentkort på en och samma order med flera leveranser förhindrar att beställningar görs.

<u>Steg som ska återskapas</u>:

1. Installera en ren version av Adobe Commerce.
1. Skapa en enkel produkt till priset 100 USD och en annan enkel produkt till priset 10 USD.
1. Logga in på [!UICONTROL Admin panel] och skapa två presentkort.

   * 02 kB8M0H0GRD = $50
   * 00GXM6SUGBLW = $25

1. Skapa en kund med två adresser.
1. Lägg två produkter i kundvagnen.

   * Lägg till produkten $10 först och lägg sedan till produkten $100. Utgåvan kan inte reproduceras om produkten $100 läggs till först.

1. Gå till kundvagnen och lägg till de två presentkorten du skapade.
1. Klicka på **[!UICONTROL Ship to Multiple Addresses]** på kundvagnssidan.
1. Tilldela varje produkt till en annan adress.
1. Gå till **[!UICONTROL Shipping information]** sida.
1. Gå till **[!UICONTROL Billing information]** sida.
1. Gå till **[!UICONTROL Review Your Order]** där du kan se problemet.
1. Försök att lägga ordern.

<u>Förväntade resultat</u>:

* Presentkort används korrekt på det totala beloppet.
* Beställningar placeras.

<u>Faktiska resultat</u>:

Presentkortsbelopp blandas med ett fel *&quot;Korrigera presentkortskoden.&quot;* vid beställning.

* Första produkten:

   * Ta bort presentkort (00GXM6SUGBLW) - $15.00
   * Ta bort presentkort (02 kB8M0H0GRD) - $0,00

* Andra produkten:

   * Ta bort presentkort (00GXM6SUGBLW) - $25.00
   * Ta bort presentkort (02 KB8M0H0GRD) - 35,00 USD

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
