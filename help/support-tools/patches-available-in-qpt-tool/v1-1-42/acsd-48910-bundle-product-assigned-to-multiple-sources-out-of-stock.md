---
title: 'ACSD-48910: Paketerad produkt som tilldelats flera källor lämnar lagret efter faktura och leverans'
description: Använd patchen ACSD-48910 för att åtgärda Adobe Commerce-problemet där den paketerade produkt som tilldelats flera källor går ut ur lagret efter att en order har fakturerats och skickats, även om den fortfarande har en kvantitet som inte är noll.
feature: Products, Inventory
role: Admin, Developer
exl-id: 6ac3dedf-1c28-4874-b963-44a429b37983
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-48910: Paketerad produkt som tilldelats flera källor lämnar lagret efter faktura och leverans

Korrigeringen ACSD-48910 åtgärdar ett problem där den paketerade produkt som tilldelats flera källor lämnar lagret efter att en order har fakturerats och skickats, även om den fortfarande har en kvantitet som inte är noll. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 är installerat. Korrigerings-ID är ACSD-48910. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den paketerade produkt som tilldelats till flera källor går ut ur lagret efter fakturering och leverans, även om den fortfarande är tillgänglig.

<u>Steg som ska återskapas</u>:

1. Skapa två webbplatser.
1. Skapa två butiker/butiksvyer (en per webbplats).
1. Skapa två enkla produkter (kvantitet = 10) och tilldela dem till både lager och webbplatser.
1. Skapa en paketerad produkt och lägg till dessa enkla produkter i den. Tilldela den paketerade produkten till båda webbplatserna.
1. Gå till butiken och lägg den paketerade produkten i kundvagnen.
1. Checka ut och beställ.
1. Fakturera och skicka ordern från administratören.

<u>Förväntade resultat</u>:

Den paketerade produkten finns kvar i lager eftersom vi bara köpte 1 av 10 artiklar.

<u>Faktiska resultat</u>:

Den paketerade produkten ändrar sin status till en produkt som inte finns i lager.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
