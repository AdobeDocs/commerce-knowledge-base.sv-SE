---
title: 'ACSD-46683: Leveranspriset anges *Inte beräknat ännu*'
description: Använd patchen ACSD-46683 för att åtgärda Adobe Commerce-problemet där fraktpriset visar *ännu ej beräknat*.
exl-id: 77986612-87b7-4f50-afaf-1cfe9a4feb6f
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683: Leveranspriset visar *Inte beräknat än*

Korrigeringen ACSD-46683 åtgärdar ett problem där leveranspriset visar *Inte beräknat än*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 har installerats. Korrigerings-ID är ACSD-46683. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Leveranspriset visar *Inte beräknat än*.

<u>Förutsättningar</u>:

Adobe Commerce Inventory management-moduler (MSI) är installerade.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt och ange priset till *$34*.
1. Konfigurera leveransmetoden för fri frakt.
1. Konfigurera minst en leveransmetod till.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** och skapa en ny regel:
   * Namn = *75more*
   * Kupong = Ingen
   * Prioritet = 1
   * Villkor: Delsumman är lika med eller större än *$75*
   * Funktionsmakron:
      * Ansök om leveransbelopp = Ja
      * Ignorera efterföljande regler = Nej
      * Fri frakt = För försändelser med matchande artiklar
1. Skapa en annan kundvagnsprisregel:
   * Namn = *35off*
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
1. I leveranssteget väljer du **$0 - fri frakt** och fortsätter till betalningssteget.
1. Kontrollera [!UICONTROL Order Summary] i betalningssteget. Den visar *[!UICONTROL $0 - Free Shipping - Free]*.
1. Använd kupongkoden *35off*, den uppdaterar delsumman och gör den mindre än $75.
1. Kontrollera [!UICONTROL Order Summary] i betalningssteget.

<u>Förväntade resultat</u>:

Följande meddelande visas: *Den valda leveransmetoden är inte tillgänglig. Välj en annan leveransmetod för den här ordern.*

<u>Faktiska resultat</u>:

Leveranspriset visar *Inte beräknat än*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
