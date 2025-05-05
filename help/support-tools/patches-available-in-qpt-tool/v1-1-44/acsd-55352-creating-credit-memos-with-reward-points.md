---
title: 'ACSD-55352: Skapa kreditnotor med belöningspoäng'
description: Använd patchen ACSD-55352 för att åtgärda Adobe Commerce-problemet där orderstatusen ändras till *stängd* och kreditnotalternativen försvinner från adminordersidan när en del av kreditnotan med kundbelöningspoäng har skapats.
feature: Checkout, Orders
role: Admin, Developer
exl-id: 33ceb2e9-3cd5-4472-941a-e06c5c534f4a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-55352: Skapa kreditnotor med belöningspoäng

Korrigeringsfilen ACSD-55352 åtgärdar ett problem där orderstatusen ändras till *stängd* när en del av kreditnotan med kundbelöningspunkter har skapats och alternativen för kreditnota försvinner från adminordersidan. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 har installerats. Korrigerings-ID är ACSD-55352. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du har skapat en partiell kreditnota med kundbelöningspunkter ändras orderstatusen till *stängd* och kreditnotalternativen försvinner från sidan med administratörsorder.

<u>Steg som ska återskapas</u>:

1. Logga in på Adobe Commerce Admin.
2. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Lägg till två frekvenser:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Poäng till valuta*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Valuta till punkter*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Skapa en enkel produkt med priset *$100* och med *Kvantitet* : *100*.
5. Skapa en kund från butiken.
6. Gå till serverdelen igen: **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Lägg till *100* och spara kunden.
7. Gå till butiken och logga in som kunden skapade tidigare.
8. Lägg produkten i varukorgen med *Antal* : *10*.
9. Gå till **[!UICONTROL Checkout]** och använd de tillgängliga *100* belöningspoängen när du uppmanas till det och placera ordern.
10. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** och skicka den beställningen.
11. Gå till [!UICONTROL Credit Memo] och uppdatera *Kvantiteten att återbetala* till *8*.
12. Markera kryssrutan **[!UICONTROL Refund Reward Points]** och klicka på **[!UICONTROL Refund offline]**.
13. Försök att återbetala de andra två återstående produkterna från beställningen med hjälp av [!UICONTROL Credit Memo].

<u>Förväntade resultat</u>:

* Admin skapar [!UICONTROL Credit Memo] för att returnera de återstående två produkterna.
* Orderstatusen är *Slutförd*.

<u>Faktiska resultat</u>:

* Det går inte att skapa fler [!UICONTROL Credit Memo].
* Orderstatusen är *Stängd*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
