---
title: '"ACSD-47232: kupong tillämpas inte när [!UICONTROL Same as Billing Address] är markerad'''
description: Använd patchen ACSD-47232 för att åtgärda Adobe Commerce-problemet där kupong inte används när [!UICONTROL Same as Billing Address] är markerad.
exl-id: 29b95a0b-8792-4830-a1e5-ce977f8453ec
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232: Kupongen används inte när [!UICONTROL Same as Billing Address] är markerad

Korrigeringsfilen ACSD-47232 åtgärdar ett problem där kupongen inte används när **[!UICONTROL Same as Billing Address]** är markerad. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 är installerat. Korrigerings-ID är ACSD-47232. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kupongen används inte när **[!UICONTROL Same as Billing Address]** är markerad.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce.
1. Skapa en enkel produkt med vikt = *8*.
1. Skapa en ny kund med standardadress för fakturering och leverans.
1. Skapa en kundprisregel med en kupong.
   * I **[!UICONTROL Conditions]** avsnitt, lägga till *Total vikt är lika med eller större än 5*
1. Försök skapa en ny order i [!UICONTROL Commerce] Admin.
   * Använd den kund du skapat just nu
   * Lägg till en produkt
   * Försök att använda kupongen

<u>Förväntade resultat</u>:

Kupongen tillämpas.

<u>Faktiska resultat</u>:

Du får ett fel som liknar följande: *Kupongkoden 123 är inte giltig. Kontrollera koden och försök igen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
