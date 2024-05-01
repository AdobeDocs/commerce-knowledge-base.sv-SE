---
title: "ACSD-51683: Det går inte att lägga till anpassningsbara alternativ i kundvagnen med GraphQL"
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

Korrigeringen ACSD-51683 åtgärdar ett problem där det anpassningsbara alternativet inte kan läggas till i kundvagnen med GraphQL. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 är installerat. Korrigerings-ID är ACSD-51683. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det anpassningsbara alternativet kan inte läggas till i kundvagnen med GraphQL.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt med en anpassningsbar **Textfält** alternativ.
1. [Lägg i kundvagnen](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) den skapade produkten med det anpassningsbara alternativet via GraphQL.
1. Skicka [kundvagn](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) GraphQL begär att få kontrollera produkten och dess detaljer i kundvagnen.

<u>Förväntade resultat</u>

The `Customizable_options` i GraphQL svar innehåller de data som anges när produkten läggs till i kundvagnen.

<u>Faktiska resultat</u>

The `Customizable_options` -avsnittet i GraphQL-svaret är tomt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
