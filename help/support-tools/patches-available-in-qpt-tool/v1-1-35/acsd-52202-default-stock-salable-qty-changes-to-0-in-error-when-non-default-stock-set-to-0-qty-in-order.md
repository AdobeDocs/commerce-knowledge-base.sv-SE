---
title: 'ACSD-52202: Standardvärdet för lagersaldokvantitet ändras till 0 om icke-standardlagervärdet är 0 i ordning.'
description: Använd patchen ACSD-52202 för att åtgärda Adobe Commerce-problemet där standardkvantiteten för lagerförsäljning ändras till 0 om standardvärdet för lagersaldo är 0.
feature: Inventory, Products
role: Admin
exl-id: 8a3b5da4-cf16-41c8-b2d5-b740d638c745
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52202: Standardvärdet för lagerförsäljningsvärde ändras till 0 om icke-standardlagervärdet är 0 i en order

Korrigeringen ACSD-52202 åtgärdar ett problem där en standardkvantitet (kvantitet) för lagerförsäljning ändras till 0 om icke-standardlager ställs in på 0 i en order. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 är installerat. Korrigerings-ID är ACSD-52202. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Standardlagerförsäljningsvärdet ändras till 0 om icke-standardlagervärdet är 0 i en order.

<u>Steg som ska återskapas</u>:

1. Logga in på [!DNL Admin].
1. Skapa **webbplats2**.
1. Skapa anpassad **källa2**.
1. Skapa anpassad **stock2**.
1. Tilldela **källa2** och **stock2** till **webbplats1** och standardkällan och standardresursen till standardwebbplatsen.
1. Skapa en enkel produkt och tilldela **kvantitet** = *10* för standardkälla och **kvantitet** = *1* för **källa2** källa.
1. Beställ med **kvantitet** = *1* for **webbplats2**.
1. Skapa en faktura och en leverans.
1. Kontrollera den enkla produkten **försäljningsbar kvantitet**.

<u>Förväntade resultat</u>:

The **försäljningsbar kvantitet** = *10* for **källa2**.

<u>Faktiska resultat</u>:

The **försäljningsbar kvantitet** = *0* för båda källorna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
