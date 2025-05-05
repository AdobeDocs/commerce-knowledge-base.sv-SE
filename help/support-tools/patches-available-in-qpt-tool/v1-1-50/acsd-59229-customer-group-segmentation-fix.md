---
title: 'ACSD-59229: Felallokering av kundgruppsdata på grund av ett inaktuellt X-Magento-Vary-värde'
description: Använd patchen ACSD-59229 för att åtgärda Adobe Commerce-problemet där kundgruppsrelaterad information sparas i fel segment på grund av ett inaktuellt X-Magento-Vary-värde i begäran.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
exl-id: 090b674a-5103-48cd-9426-41166bf9272c
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-59229: Felallokering av kundgruppsdata på grund av ett inaktuellt X-Magento-Vary-värde

Korrigeringen ACSD-59229 åtgärdar ett problem där kundgruppsrelaterad information sparas i fel segment på grund av ett inaktuellt X-Magento-Vary-värde i begäran. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 har installerats. Korrigerings-ID är ACSD-59229. Observera att problemet är åtgärdat i 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundgruppsrelaterad information sparas i fel segment på grund av ett inaktuellt X-Magento-Vary-värde i begäran.

<u>Förutsättningar</u>:

Kontrollera att Adobe Commerce B2B med exempeldata är installerat och att [!DNL Varnish] har konfigurerats.

<u>Steg som ska återskapas</u>:

1. Ange avancerade priser för [!DNL SKU 24-MB01]:
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *Partihandel* = *$200*
      * *Återförsäljare* = *$30*

1. Skapa två kundkonton.
1. Tilldela båda kunderna till gruppen **Partihandel**.
1. Öppna två olika webbläsarsessioner och logga in med varje kund.
1. Navigera till produktsidan **[!UICONTROL 24-MB01]** för varje kund och verifiera att priset som visas är *$200*.
1. Ändra kundgruppen för en av kunderna till **Återförsäljare**.
1. Rensa cachen med kommandot: `bin/magento cache:flush full_page`.
1. Uppdatera produktsidan för varje kund.

<u>Förväntade resultat</u>:

1. Återförsäljaren kan se rätt pris på *$30* för produkten.
1. Grossistkunden kan se rätt pris på *$200* för produkten.

<u>Faktiska resultat</u>:

1. Återförsäljaren kan se rätt pris på *$30* för produkten.
1. Grossistkunden ser ett felaktigt pris på *$30* (detaljhandelspris) för produkten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
