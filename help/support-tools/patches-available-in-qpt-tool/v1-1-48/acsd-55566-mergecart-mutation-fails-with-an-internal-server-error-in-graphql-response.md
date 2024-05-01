---
title: '"ACSD-55566: [!UICONTROL mergeCart] mutation misslyckas med internt serverfel i [!DNL GraphQL] response'''
description: Använd korrigeringsfilen ACSD-5566 för att åtgärda Adobe Commerce-problemet där mutationen "mergeCart" misslyckas med ett internt serverfel i [!DNL GraphQL] svar när källan och målvagnarna som har samma paketobjekt sammanfogas.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84a9b861-351e-4fcc-bb91-3e31c7ae24e6
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-5566: `mergeCart` mutation misslyckas med internt serverfel i [!DNL GraphQL] svar

Korrigeringen ACSD-5566 åtgärdar ett problem där `mergeCart` mutationen misslyckas med ett internt serverfel i [!DNL GraphQL] svar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 är installerat. Korrigerings-ID:t är ACSD-5566. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`mergeCart` mutationen misslyckas med ett internt serverfel i [!DNL GraphQL] svar när källan och målvagnarna som har samma paketobjekt sammanfogas.

<u>Steg som ska återskapas</u>:

1. Skapa en anpassad källa och en anpassad Stock.
1. Tilldela det skapade arkivet till huvudwebbplatsen.
1. Skapa en enkel produkt och tilldela den skapade källan till den (qty=2).
1. Skapa en paketprodukt med ett alternativ och en underordnad produkt (produkt skapad i steg 3).
1. Skapa en gästvagn via [!DNL GraphQL].
1. Lägg till en paketprodukt med båda alternativen markerade.
1. Spara *cartID*.
1. Skapa en kund och generera en kundtoken.
1. Skapa en kundvagn.
1. Lägg samma paketprodukt med samma konfiguration i kundvagnen.
1. Försök att sammanfoga gästvagnen med kundvagnen.

<u>Förväntade resultat</u>:

Kundvagnen innehåller produkter från båda vagnarna.

<u>Faktiska resultat</u>:

Du får ett internt fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
