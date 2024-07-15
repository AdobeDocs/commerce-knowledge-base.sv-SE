---
title: 'ACSD-46674: anpassade alternativ för bildtyp som visas som HTML i kundens e-postmeddelanden'
description: Använd patchen ACSD-46674 för att åtgärda Adobe Commerce-problemet där anpassade alternativ för bildtyp visas som HTML i kundens e-postmeddelanden.
exl-id: b4941dd0-bb3a-4805-9631-1d256a92f461
feature: Communications, Personalization
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-46674: anpassade alternativ för bildtyp som visas som HTML i kundmeddelanden

Korrigeringen ACSD-46674 åtgärdar ett problem där anpassade alternativ för en bildtyp visas som HTML i kundens e-postmeddelanden. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 har installerats. Korrigerings-ID är ACSD-46674. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Anpassade alternativ för en bildtyp visas som HTML i kundens e-postmeddelanden.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt med ett anpassat alternativ.
   * Alternativtyp: *Fil*
   * Kompatibla filtillägg: *png, jpg, gif*
   * Obligatoriskt: *Ja*
1. Gör en beställning för den här produkten med en bild som har överförts som ett anpassat alternativ.
1. Skapa en faktura för den order som skapades i steg två.
1. Skapa en kreditnota.
1. Kontrollera alla bekräftelsemeddelanden.

<u>Förväntade resultat</u>:

Bekräftelsemeddelandena visar den överförda bilden.

<u>Faktiska resultat</u>:

Bekräftelsemeddelandena innehåller oformaterad HTML-kod i stället för en bild med anpassade produktalternativ.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tools] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i [!DNL QPT] finns i [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
