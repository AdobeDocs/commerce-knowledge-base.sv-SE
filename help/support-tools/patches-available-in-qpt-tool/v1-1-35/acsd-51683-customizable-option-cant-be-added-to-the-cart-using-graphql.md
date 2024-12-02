---
title: 'ACSD-51683: Det går inte att lägga till det anpassningsbara alternativet i kundvagnen med GraphQL'
description: Använd patchen ACSD-51683 för att åtgärda Adobe Commerce-problemet där det anpassningsbara alternativet inte kan läggas till i kundvagnen med GraphQL.
feature: GraphQL
role: Admin
exl-id: 4de0d8b7-714e-4bbf-8a0d-bb6e0c3aae55
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51683: Det går inte att lägga till det anpassningsbara alternativet i kundvagnen med GraphQL

Korrigeringen ACSD-51683 åtgärdar ett problem där det anpassningsbara alternativet inte kan läggas till i kundvagnen med GraphQL. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 har installerats. Korrigerings-ID är ACSD-51683. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det anpassningsbara alternativet kan inte läggas till i kundvagnen med GraphQL.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt med ett anpassningsbart **textfält**-alternativ.
1. [Lägg till den skapade produkten i varukorgen](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) med det anpassningsbara alternativet via GraphQL.
1. Skicka GraphQL-förfrågan [kundvagn](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) för att kontrollera produkten och dess information i kundvagnen.

<u>Förväntade resultat</u>

Avsnittet `Customizable_options` i GraphQL-svaret innehåller de data som angavs när produkten lades till i kundvagnen.

<u>Faktiska resultat</u>

Avsnittet `Customizable_options` i GraphQL-svaret är tomt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
