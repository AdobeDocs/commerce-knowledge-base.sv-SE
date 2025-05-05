---
title: 'ACSD-56447: Om du lägger till samma produkt i kundvagnen via en parallell webb-REST API resulterar det i två separata artiklar i kundvagnen'
description: Använd patchen ACSD-56447 för att åtgärda Adobe Commerce-problemet, där det uppstår två separata saker i kundvagnen om du lägger till samma produkt via en parallell webb-REST API-begäran.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: c63874be-a8a6-4143-adaa-ba3e9e107dd4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-56447: Om du lägger till samma produkt i kundvagnen via en parallell webb-REST API resulterar det i två separata artiklar i kundvagnen

Korrigeringen ACSD-56447 åtgärdar ett problem där det uppstår två separata saker i kundvagnen om samma produkt läggs till i vagnen via en parallell webb-REST API-begäran. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 har installerats. Korrigerings-ID är ACSD-56447. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du lägger till samma produkt i kundvagnen via parallella webb-REST API-förfrågningar blir det två separata artiklar i kundvagnen.

<u>Steg som ska återskapas</u>:

1. Generera en kundtoken för att göra REST API-anropsbegäran med [!DNL Postman].
1. Skapa en kundvagn för kunden.
1. Använd den token som genereras ovan för att skapa en tom kundvagn.
1. Använd CURL för att göra två `AddProductsToCart`-begäranden parallella. Följ instruktionerna i [Beställningssjälvstudiekursen](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) i utvecklardokumentationen.

<u>Förväntade resultat</u>:

Objekt med flera kvantiteter visas på en rad.

<u>Faktiska resultat</u>:

Samma SKU:er visas i flera radobjekt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
