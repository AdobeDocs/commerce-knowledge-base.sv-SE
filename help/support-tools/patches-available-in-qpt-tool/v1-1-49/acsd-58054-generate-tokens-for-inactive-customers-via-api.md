---
title: 'ACSD-58054: API-tokengenerering för inaktiva kunder'
description: Använd patchen ACSD-58054 för att åtgärda Adobe Commerce-problemet där det är möjligt att generera kundtoken för inaktiva kunder via API.
feature: Customers, API Mesh
role: Admin, Developer
source-git-commit: 70f90884d8106719934b007b2e33f033e1b7e2b2
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ACSD-58054: API-tokengenerering för inaktiva kunder

Korrigeringen ACSD-58054 åtgärdar ett problem där det går att generera kundtoken för inaktiva kunder via API. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 har installerats. Korrigerings-ID är ACSD-58054. Observera att problemet är planerat att åtgärdas i B2B 1.5.1.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Inaktiv generering av kundtoken via API.

<u>Förutsättningar</u>:

B2B-modulerna är installerade.

<u>Steg som ska återskapas</u>:

1. Skapa ett kundkonto.
1. Skapa en kundtoken med API.
1. Navigera till serverdelen och inaktivera kundkontot.
1. Försök att generera en kundtoken igen.

<u>Förväntade resultat</u>:

Ingen token genereras.

<u>Faktiska resultat</u>:

En token genereras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
