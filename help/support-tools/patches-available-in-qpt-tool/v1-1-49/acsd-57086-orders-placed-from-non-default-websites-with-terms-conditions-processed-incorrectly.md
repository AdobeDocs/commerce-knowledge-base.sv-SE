---
title: 'ACSD-57086: Order från icke-standardwebbplatser med villkor aktiverade behandlas felaktigt'
description: Använd patchen ACSD-57086 för att åtgärda Adobe Commerce-problemet där beställningar från icke-standardwebbplatser med aktiverade villkor inte behandlas korrekt.
feature: Orders
role: Admin, Developer
source-git-commit: ab90568b0333415e73ca42b9c127a2a599f00aa7
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---


# ACSD-57086: Beställningar från webbplatser som inte är standard och där villkor är aktiverade behandlas felaktigt

Korrigeringen ACSD-57086 åtgärdar ett problem där beställningar från icke-standardwebbplatser med aktiverade villkor inte behandlas korrekt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 har installerats. Korrigerings-ID är ACSD-57086. Observera att detta problem har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du använder en konfiguration för flera butiker med AsyncOrder-bearbetning avvisas beställningar som gjorts på andra webbplatser/butiker än huvudwebbplatsen på grund av problem med scopehantering i kundkoden.

<u>Steg som ska återskapas</u>:

1. Installera [!DNL RabbitMQ] och kör `bin/magento setup:upgrade` för att skapa köerna för [!DNL RabbitMQ].
1. Konfigurera AsyncOrder-bearbetning med:

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. Skapa en sekundär webbplats, en butik och en butiksvy.
1. Skapa en produkt som delas mellan båda webbplatserna.
1. Aktivera villkor:
   1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
   1. Ange *[!UICONTROL Enable Terms And Conditions]* som *Ja*.
1. Konfigurera villkor för båda webbplatserna:
   1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**.
   1. Använd följande inställningar:
      * *[!UICONTROL Condition Name]*: *Allt*
      * *[!UICONTROL Status]*: *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]*: *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]*: *[!UICONTROL Default Store View]*
   1. Skapa ett annat villkor för den andra webbplatsvyn/butiksvyn.
1. Ändra standardwebbplatsen genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**. Klicka på den andra webbplatsen, kontrollera *[!UICONTROL Set as Default]* och spara.
1. Rensa cachen med:

   ```bash
   bin/magento cache:clear
   ```

1. Gå till butiken och lägg till en produkt i kundvagnen. Fortsätt till kassan och gör en beställning (du bör se en kryssruta i steget med betalningsmetoden för att acceptera villkoren).
1. Gå tillbaka till Admin när du har gjort beställningen och ändra standardwebbplatsen till den ursprungliga huvudwebbplatsen och spara.
1. Rensa cachen:

   ```bash
   bin/magento cache:clear
   ```

1. Kör följande kommando för att starta kökonsumenten:

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>Förväntade resultat</u>:

Beställningen är klar. Den avvisas inte automatiskt.

<u>Faktiska resultat</u>:

Orderstatus är *avvisad* med följande kommentar:

*Ordern har inte monterats. Godkänn först villkoren och försök sedan att göra din beställning igen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
