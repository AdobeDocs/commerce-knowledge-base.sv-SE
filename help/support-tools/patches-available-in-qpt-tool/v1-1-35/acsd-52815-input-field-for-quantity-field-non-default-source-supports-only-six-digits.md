---
title: 'ACSD-52815: Indatafältet för kvantitetsfält från en icke-standardkälla stöder endast upp till 6 siffror'
description: Använd patchen ACSD-52815 för att åtgärda prestandaproblemet i Adobe Commerce där indatafältet för kvantitetsfältet för en icke-standardkälla endast stöder upp till 6 siffror, till skillnad från 8 för standardlager.
feature: Inventory, Products
role: Admin
exl-id: 44fda5ef-cb8a-481a-9112-f36d886ae3db
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52815: Indatafältet för kvantitetsfält för icke-standardkälla stöder endast upp till 6 siffror

Korrigeringen ACSD-52815 åtgärdar ett problem där indatafältet för kvantitetsfältet för en icke-standardkälla endast stöder upp till 6 siffror, till skillnad från 8 för ett standardlager. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 är installerat. Korrigerings-ID är ACSD-52815. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Indatafältet för kvantitetsfältet för en icke-standardkälla stöder endast upp till 6 siffror, till skillnad från 8 för en standardlagerkälla.

<u>Steg som ska återskapas</u>:

1. Skapa en ny aktie och källa.
1. Skapa en produkt med den nya källversionen som är inställd på 123.
1. Kontrollera den säljbara kvantiteten (123).
1. Uppdatera källkvantiteten till 12345678.
1. Kontrollera den säljbara kvantiteten igen.

<u>Förväntade resultat</u>:

Försäljningsbar kvantitet visar rätt belopp.

<u>Faktiska resultat</u>:

Den säljbara kvantiteten är 999999,9999.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
