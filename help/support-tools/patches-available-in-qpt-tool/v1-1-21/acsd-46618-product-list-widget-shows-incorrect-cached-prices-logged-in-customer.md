---
title: "ACSD-46618: produktlistwidgeten visar felaktiga cachelagrade priser för inloggad kund"
description: Använd en patch för att åtgärda problemet med Adobe Commerce där produktlistwidgeten visar felaktiga cachelagrade priser för en inloggad kund.
exl-id: 8b182822-1d3d-4793-871b-cdf4565d0712
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-46618: Widgeten Produktlista visar felaktiga cachelagrade priser för en inloggad kund

Korrigeringen ACSD-46618 löser problemet där produktlistwidgeten visar felaktiga cachelagrade priser för en inloggad kund. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21 är installerat. Korrigerings-ID är ACSD-46618. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Korrigeringen ACSD-46618 löser problemet där produktlistwidgeten visar felaktiga cachelagrade priser för en inloggad kund.

<u>Steg som ska återskapas</u>:

1. I Adobe Commerce Admin väljer du **[!UICONTROL Stores]** sedan **[!UICONTROL Configuration]**, expandera **[!UICONTROL Sales]** och markera **[!UICONTROL Tax]**. Uppdatera skatteinställningarna för att visa priser inklusive och exklusive moms.
1. Ange **[!UICONTROL Enable Cross Border Trade]** = _Ja_.
1. Skapa en momsregel som bara gäller för USA.
1. Lägg till en widget på startsidan, inklusive mer än en produkt.
1. Skapa två kunder med en adress i USA och en adress som inte är i USA.
1. Logga in med den amerikanska kunden från butiken. Kontrollera att sidan är cachelagrad.
1. Observera priset som visas i startsideswidgeten.
1. Logga ut och logga in med en kund som inte är i USA.

<u>Förväntade resultat</u>:

Priset som visas i startsidans widget motsvarar kundens adress.

<u>Faktiska resultat</u>:

På startsidans widget visas priser med moms för kunder utanför USA.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
