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

Korrigeringen ACSD-48910 åtgärdar ett problem där den paketerade produkt som tilldelats flera källor lämnar lagret efter att en order har fakturerats och skickats, även om den fortfarande har en kvantitet som inte är noll. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 har installerats. Korrigerings-ID är ACSD-48910. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

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

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
