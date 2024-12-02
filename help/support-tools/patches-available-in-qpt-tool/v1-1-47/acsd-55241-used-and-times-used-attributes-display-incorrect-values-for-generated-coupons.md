---
title: 'ACSD-55241: **Används** och **Används**-attribut visar felaktiga värden för genererade kuponger'
description: Använd patchen ACSD-55241 för att åtgärda Adobe Commerce-problemet där attributen **Used** och **Times Used** visar felaktiga värden för genererade kuponger
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: f830486ab3b00fca92dda897bbf0bfbae41543c1
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241: Attributen **Används** och **Används flera gånger** visar felaktiga värden för genererade kuponger

Korrigeringen ACSD-55241 åtgärdar ett problem där attributen **Används** och **Används** visar felaktiga värden för genererade kuponger. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.47 har installerats. Korrigerings-ID är ACSD-55241. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Attributen **Används** och **Används** visar felaktiga värden för genererade kuponger.

<u>Steg som ska återskapas</u>:

1. Skapa **[!UICONTROL Cart Price Rules]** från **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** och lägg till villkor som matchar när en order placeras (Exempel: delsumma större än *5$*)

   * Använd rabatt.
   * Välj **[!UICONTROL Auto Coupon]**.
   * Det genererar några kupongkoder från **Hantera kupongkoder**.
   * Indexera om och rensa cachen.

1. Skapa en **[!UICONTROL customer account]** och logga in på frontend.
1. Lägg en produkt med mer än *2* kvantiteter i kundvagnen och använd en kupong.
1. Klicka på **[!UICONTROL Check Out with Multiple Addresses]**.
1. Välj en separat adress för varje kvantitet, placera ordern och slutför utcheckningsprocessen.
1. Observera ordersumman från administratören och se vilken rabatt som tillämpas.
1. Lägg en ny order med en annan kupong.
1. Kör kommandot `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` om du vill uppdatera användningen av kupongkoden.

<u>Förväntade resultat</u>:

Rätt antal ska visas i kolumnerna **Tid använd** och **Använd** med värdet **Ja** för **[!UICONTROL manage coupon]** i **[!UICONTROL cart price rule]** i administratören.

<u>Faktiska resultat</u>:

Det använda kupongkodsantalet uppdateras inte i kolumnen **Använd tid** i kupongrutnätet, och i kolumnen **Används** visas värdet *Nej* om du gör en beställning med flera leveransadresser.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
