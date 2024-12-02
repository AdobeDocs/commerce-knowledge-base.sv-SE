---
title: 'ACSD-48784: Kundsegmentpriser cachelagrades felaktigt mellan kundgrupper'
description: Använd patchen ACSD-48784 för att åtgärda problemet med Adobe Commerce där kundsegmentpriserna cachas felaktigt mellan kundgrupper.
exl-id: 6be11fd0-5c93-4ac7-8664-7e2a289c9e38
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48784: Kundsegmentpriser cachelagrades felaktigt mellan kundgrupper

Korrigeringen ACSD-48784 åtgärdar ett problem där kundsegmentpriser cachas felaktigt mellan kundgrupper. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 har installerats. Korrigerings-ID är ACSD-48784. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundsegmentpriser cachelagras felaktigt mellan kundgrupper.

<u>Förutsättningar</u>:

Konfigurera [!DNL Varnish] eller [!DNL Fastly].

<u>Steg som ska återskapas</u>:

1. Aktivera cachelagring av hela sidor i din butik.
1. Logga in på webbplatsen som en användare med ett särskilt kundgruppspris.
1. Gå till en produktsida för en produkt med ett särskilt kundgruppspris. Observera *specialpriset*.
1. Öppna samma produktsida som en gästanvändare i en separat webbläsare utan att logga in. Tänk på normalpriset.
1. Gå till Adobe Commerce administratörsgränssnitt och rensa Adobe Commerce- och [!DNL Fastly]-cachen för den här butiken.
1. Ta bort cookien `X-Magento-Vary` i den inloggade webbläsaren.
1. I den inloggade webbläsaren läser du in samma produktsida flera gånger tills cachningen är helt tömd.
1. I den webbläsare som inte är inloggad läser du in produktsidan igen för att se kundgruppspriserna.

<u>Förväntade resultat</u>:

På produktsidan visas rätt pris för specifika kundgrupper.

<u>Faktiska resultat</u>:

* Gästanvändare ser det speciella inloggade användarpriset.
* Mini-vagnen visar rätt pris när produkten har lagts till.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
