---
title: 'ACSD-55241: **Används** och **Används i tider** visar felaktiga värden för genererade kuponger'
description: Använd patchen ACSD-55241 för att åtgärda Adobe Commerce-problemet där attributen **Used** och **Times Used** visar felaktiga värden för genererade kuponger
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: 5d0b4743fe49d22c099102490f93dc4065ab4413
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-5241: **Används** och **Använda tider** attribut visar felaktiga värden för genererade kuponger

Korrigeringen ACSD-55241 åtgärdar ett problem där **Används** och **Använda tider** attribut visar felaktiga värden för genererade kuponger. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.47 är installerat. Korrigerings-ID är ACSD-55241. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

**Används** och **Använda tider** attribut visar felaktiga värden för genererade kuponger.

<u>Steg som ska återskapas</u>:

1. Skapa **[!UICONTROL Cart Price Rules]** från **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** och lägga till villkor som matchar när en order placeras (Exempel: delsumma större än *5$*)

* Använd rabatt.
* Välj **[!UICONTROL Auto Coupon]**.
* Det genererar några kupongkoder från **Hantera kupongkoder**.
* Indexera om och rensa cachen.

1. Skapa en **[!UICONTROL customer account]** och logga in på frontend.
1. Lägg till en produkt med mer än *2* Kvantiteterna i varukorgen och en kupong.
1. Klicka på **[!UICONTROL Check Out with Multiple Addresses]**.
1. Välj en separat adress för varje kvantitet, placera ordern och slutför utcheckningsprocessen.
1. Observera ordersumman från administratören och se vilken rabatt som tillämpas.
1. Lägg en ny order med en annan kupong.
1. Kör `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` om du vill uppdatera användningen av kupongkoden.

<u>Förväntade resultat</u>:

Rätt antal ska visas i **Använd tid** och **Används** kolumner med **Ja** värde för **[!UICONTROL manage coupon]** i **[!UICONTROL cart price rule]** i administratören.

<u>Faktiska resultat</u>:

Antalet använda kupongkoder uppdateras inte i **Använd tid** kolumn i kupongrutnätet, och **Används** kolumnen visar *Nej* om du gör en beställning med flera leveransadresser.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
