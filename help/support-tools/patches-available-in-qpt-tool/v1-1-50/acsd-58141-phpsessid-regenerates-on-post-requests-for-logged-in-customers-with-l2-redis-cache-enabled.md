---
title: 'ACSD-58141: PHPSESSID återskapar begäranden om POST för inloggade kunder med L2 Redis-cache aktiverat'
description: Använd patchen ACSD-58141 för att åtgärda Adobe Commerce-problemet där PHESSID återskapas vid förfrågningar från POSTER på Storefront för en inloggad kund med L2 Redis-cache aktiverad och kunden uppdateras från Admin.
feature: Customers, Cache
role: Admin, Developer
source-git-commit: 488699c5d880baee2f7191d963368415f90c3340
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# ACSD-58141: PHPSESSID återskapar [!DNL POST]-begäranden för inloggade kunder om L2 Redis-cache är aktiverad

Korrigeringen ACSD-58141 åtgärdar ett problem där `PHPSESSID` återskapar [!DNL POST]-begäranden för en inloggad kund om L2 Redis-cachen är aktiverad och kunden uppdateras från Admin. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 har installerats. Korrigerings-ID är ACSD-58141. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce och Magento Open Source:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`PHPSESSID` återskapar [!DNL POST] begäranden för en inloggad kund med L2 Redis-cache aktiverad.

<u>Förutsättningar</u>

Miljön måste konfigureras med Redis som har minst tre noder.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Skapa en kund och logga in på Storefront.
1. Kontrollera värdet för `PHPSESSID`.
1. Skicka några [!DNL POST] förfrågningar (t.ex. om du lägger till produkten i kundvagnen) och se att `PHPSESSID` inte ändras).
1. Logga in på panelen **[!UICONTROL Admin]** och ändra kundens mellannamn.
1. När mellannamnet sparas ändrar du det och sparar det igen några gånger.
1. Skicka en [!DNL POST]-begäran i butiken. `PHPSESSID` borde ha uppdaterats.
1. Skicka ytterligare en [!DNL POST]-begäran i butiken och kontrollera `PHPSESSID`.
1. Upprepa föregående steg några gånger.

<u>Förväntade resultat</u>

`PHPSESSID` genereras bara om en gång efter att kunddata har ändrats.

<u>Faktiska resultat</u>:

`PHPSESSID` genereras om varje gång [!DNL POST]-begäranden skickas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
