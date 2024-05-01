---
title: 'ACSD-46683: Leveranspriset anges *ännu ej beräknat*'
description: Använd patchen ACSD-46683 för att åtgärda Adobe Commerce-problemet där fraktpriset visar *ännu ej beräknat*.
exl-id: 77986612-87b7-4f50-afaf-1cfe9a4feb6f
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683: Leveranspriser *Inte beräknat ännu*

Korrigeringen ACSD-46683 åtgärdar ett problem där fraktpriset anger *Inte beräknat ännu*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 är installerat. Korrigerings-ID är ACSD-46683. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Leveranspriset *Inte beräknat ännu*.

<u>Förutsättningar</u>:

Adobe Commerce Inventory management-moduler (MSI) är installerade.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt och ange priset till *34 dollar*.
1. Konfigurera leveransmetoden för fri frakt.
1. Konfigurera minst en leveransmetod till.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** och skapa en ny regel:
   * Namn = *75more*
   * Kupong = Ingen
   * Prioritet = 1
   * Villkor: Delsumman är lika med eller större än *75 dollar*
   * Funktionsmakron:
      * Ansök om leveransbelopp = Ja
      * Ignorera efterföljande regler = Nej
      * Fri frakt = För försändelser med matchande artiklar
1. Skapa en annan kundvagnsprisregel:
   * Namn = *35 rabatt*
   * Prioritet = 0
   * Kupong = Specifik kupong
   * Kupongkod = 35off
   * Funktionsmakron:
      * Använd = Procent av produktprisrabatt
      * Rabattbelopp = 35
      * Tillämpa på leveransbelopp = Nej
      * Ignorera efterföljande regler = Ja
      * Fri frakt = Nej
1. Öppna butiken och lägg till tre produkter i kundvagnen så att delsumman överstiger 75 dollar.
1. Gå till kassan som gäst.
1. I leveranssteget väljer du **$0 - fri frakt** och gå vidare till betalningssteget.
1. Kontrollera [!UICONTROL Order Summary] på betalningssteget. Det syns *[!UICONTROL $0 - Free Shipping - Free]*.
1. Använda kupongkoden *35 rabatt*, uppdateras delsumman och blir mindre än 75 dollar.
1. Kontrollera [!UICONTROL Order Summary] på betalningssteget.

<u>Förväntade resultat</u>:

Följande meddelande visas: *Den valda leveransmetoden är inte tillgänglig. Välj en annan leveransmetod för den här ordern.*

<u>Faktiska resultat</u>:

Fraktpriset visas *Inte beräknat ännu*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
