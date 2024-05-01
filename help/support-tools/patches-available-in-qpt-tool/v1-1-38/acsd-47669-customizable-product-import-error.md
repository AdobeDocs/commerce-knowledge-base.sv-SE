---
title: 'ACSD-47669: Internt serverfel vid import av produkter med anpassningsbara alternativ'
description: Använd patchen ACSD-47669 för att åtgärda Adobe Commerce-problemet där det uppstår ett internt serverfel vid import av produkter med anpassningsbara alternativ.
feature: Products
role: Admin, Developer
exl-id: 14afbd71-075a-4264-8da2-dbbd93f472a1
source-git-commit: 66e56b9ba31fd2c5d3f8a330f09d8e94df77b17d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47669: Internt serverfel vid import av produkter med anpassningsbara alternativ

Korrigeringen ACSD-47669 åtgärdar ett problem där det uppstår ett internt serverfel under produktimporter med anpassningsbara alternativ. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.38 är installerat. Korrigerings-ID är ACSD-47669. Observera att problemet redan har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det finns ett internt serverfel när du importerar produkter med anpassningsbara alternativ.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en butiksvy. Se till att du har 2 butiksvyer, t.ex. en, UK.
1. Skapa två enkla produkter, till exempel prod1 och prod2.
1. Förbered en csv-fil som lägger till anpassade alternativ för båda produkterna i varje butiksvy och för **Alla butiksvyer** omfång. Importera den här CSV-filen.
1. Förbered en annan csv-fil som innehåller två poster. Den första posten ska vara att uppdatera de anpassade alternativen för prod1 specifikt för visningsomfånget för den brittiska butiken och den andra posten ska vara att uppdatera de anpassade alternativen för prod2 för **Alla butiksvyer** omfång. Importera den här andra csv-filen.

<u>Förväntade resultat</u>:

Du bör kunna anpassa alternativen utan fel.

<u>Faktiska resultat</u>:

Ett integritetsbegränsningsfel inträffar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
