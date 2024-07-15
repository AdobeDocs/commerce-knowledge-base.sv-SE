---
title: 'ACSD-55610: Delvis annullerad order har felaktigt rabattbelopp'
description: Använd patchen ACSD-55610 för att åtgärda Adobe Commerce-problemet där en delvis annullerad order har ett felaktigt rabattbelopp.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: f4cca4fa-dc04-4c86-9176-c648b1d0e732
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-55610: Delvis annullerad order har felaktigt rabattbelopp

Korrigeringen ACSD-55610 åtgärdar ett problem där en delvis annullerad order har ett felaktigt rabattbelopp. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.43 har installerats. Korrigerings-ID är ACSD-55610. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En delvis annullerad order har ett felaktigt rabattbelopp.

<u>Steg som ska återskapas</u>:

1. Skapa en kundvagnsprisregel.

   * *[!UICONTROL Rule Name]*: *Vinterförsäljning*
   * *[!UICONTROL Active]* = *Ja*
   * *[!UICONTROL Websites]* = *Huvudwebbplats*
   * Välj alla kundgrupper.
   * Välj en viss kupong.
   * *[!UICONTROL Coupon Code]*: *WINTER10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *Delsumma(utom. moms) är lika med eller större än 75*
   * Använd *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *Ja*

1. Skapa tre produkter med 100 priser.
1. Lägg de tre produkterna i kundvagnen.
1. Använd kupongen.
1. Beställ.
1. Fakturera en artikel i ordern och skicka den.
1. Avbryt de andra två objekten.
1. Kontrollera kolumnen `base_discount_canceled`.

<u>Förväntade resultat</u>:

Rabattbeloppet i `base_discount_cancelled` återspeglas korrekt.

<u>Faktiska resultat</u>:

`base_discount_cancelled` är inte korrekt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
