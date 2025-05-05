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

Korrigeringen ACSD-47669 åtgärdar ett problem där det uppstår ett internt serverfel under produktimporter med anpassningsbara alternativ. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.38 har installerats. Korrigerings-ID är ACSD-47669. Observera att problemet redan har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det finns ett internt serverfel när du importerar produkter med anpassningsbara alternativ.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en butiksvy. Se till att du har 2 butiksvyer, t.ex. en, UK.
1. Skapa två enkla produkter, till exempel prod1 och prod2.
1. Förbered en csv-fil som lägger till anpassade alternativ för båda produkterna i varje butiksvy och för omfattningen **All Store View** . Importera den här CSV-filen.
1. Förbered en annan csv-fil som innehåller två poster. Den första posten ska vara att uppdatera de anpassade alternativen för prod1 specifikt för visningsomfånget för den brittiska butiken och den andra posten ska vara att uppdatera de anpassade alternativen för prod2 för omfattningen **All Store View** . Importera den här andra csv-filen.

<u>Förväntade resultat</u>:

Du bör kunna anpassa alternativen utan fel.

<u>Faktiska resultat</u>:

Ett integritetsbegränsningsfel inträffar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
