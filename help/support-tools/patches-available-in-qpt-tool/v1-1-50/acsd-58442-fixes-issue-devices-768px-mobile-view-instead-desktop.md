---
title: 'ACSD-58442: Korrigerar problemet där enheter med 768 px bredd behandlas som mobila enheter, vilket gör att meny och rubrik läses in i mobilvyn och inte i skrivbordsläge'
description: Använd patchen ACSD-58442 för att åtgärda Adobe Commerce-problemet där enheter med en bredd på 768 px hanteras som mobila enheter, vilket gör att meny och rubrik läses in i mobilvyn i stället för i skrivbordsversionen.
feature: Storefront
role: Admin, Developer
source-git-commit: e1e2983f529b12002b801045ceee7264ff77d87b
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# ACSD-58442: Korrigerar problemet där enheter med 768 px bredd behandlas som mobila, vilket gör att meny och rubrik läses in i mobilvyn och inte i skrivbordsvyn

Korrigeringen ACSD-58442 åtgärdar Adobe Commerce-problemet där enheter med bredden 768 px behandlas som mobila enheter, vilket gör att meny och rubrik läses in i mobilvyn i stället för i skrivbordsversionen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 har installerats. Korrigerings-ID är ACSD-58442. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Systemet hanterar nu enheter med en bredd på 768px som stationära datorer, vilket säkerställer att meny- och rubrikerna läses in korrekt. Tidigare behandlades enheter med bredden 768 px som mobila enheter, vilket gjorde att menyn och huvudet lästes in i en mobilvy.

<u>Steg som ska återskapas</u>:

1. Läs in hemsidan på en iPad Mini eller använd webbläsarens inspektionsverktyg för att ändra storlek på webbläsaren till bredden *768px*.
1. Öppna huvudmenyn.

<u>Förväntade resultat</u>:

Meny och sidhuvud läses in som skrivbordsvy.

<u>Faktiska resultat</u>:

Meny och sidhuvud läses in som en mobilvy.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.


