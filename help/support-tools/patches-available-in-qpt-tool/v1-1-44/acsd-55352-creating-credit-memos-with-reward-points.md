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

Korrigeringen ACSD-55352 åtgärdar ett problem där orderstatusen ändras till *stängd* och alternativen för kreditnota försvinner från adminordersidan. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 är installerat. Korrigerings-ID är ACSD-55352. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du har skapat en partiell kreditnota med kundbelöningspoäng ändras orderstatusen till *stängd* och alternativen för kreditnota försvinner från adminordersidan.

<u>Steg som ska återskapas</u>:

1. Logga in på Adobe Commerce Admin.
2. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Lägg till två frekvenser:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Poäng till valuta*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Valuta till poäng*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Skapa en enkel produkt till priset av *100 dollar* och med *Antal* : *100*.
5. Skapa en kund från butiken.
6. Gå till backend igen: **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Lägg till *100* och spara kunderna.
7. Gå till butiken och logga in som kunden skapade tidigare.
8. Lägg produkten i varukorgen med *Antal* : *10*.
9. Gå till **[!UICONTROL Checkout]** och använda de tillgängliga *100* belöningspoäng när du uppmanas till detta och lägger ordern.
10. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** och skicka beställningen.
11. Gå till [!UICONTROL Credit Memo] och uppdatera *Återbetalningsbelopp* till *8*.
12. Tick the **[!UICONTROL Refund Reward Points]** kryssruta och klicka **[!UICONTROL Refund offline]**.
13. Försök att återbetala de andra två återstående produkterna från beställningen med hjälp av [!UICONTROL Credit Memo].

<u>Förväntade resultat</u>:

* Administratören skapar [!UICONTROL Credit Memo] för att returnera de två återstående produkterna.
* Orderstatusen är *Slutförd*.

<u>Faktiska resultat</u>:

* Kan inte skapa fler [!UICONTROL Credit Memo].
* Orderstatusen är *Stängd*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
