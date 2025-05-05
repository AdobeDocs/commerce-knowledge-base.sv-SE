---
title: 'ACSD-53643: Ordern har ett felaktigt belopp när en inköpsorder placeras'
description: Använd patchen ACSD-53643 för att åtgärda Adobe Commerce-problemet där ordern har ett felaktigt totalt ordervärde när en inköpsorder med inaktiverade eller färdiga produkter läggs.
feature: B2B
role: Admin, Developer
exl-id: 9843e07a-8a17-401e-98bc-559df5148d34
source-git-commit: 2356ac10b05ae9f38e5c0ca90d9156b0fc405718
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643: Ordern har ett felaktigt belopp när en inköpsorder placeras

Korrigeringen ACSD-53643 åtgärdar ett problem där ordern har ett felaktigt totalt ordervärde när en inköpsorder med inaktiverade produkter eller produkter som inte finns i lager läggs. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 har installerats. Korrigerings-ID är ACSD-53643. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ordersumman är felaktig när en inköpsorder med inaktiverade produkter eller produkter som inte finns i lager placeras.

<u>Steg som ska återskapas</u>:

1. Installera *[!UICONTROL B2B]* och *[!UICONTROL Inventory]*.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** och ange **[!UICONTROL Company]** = *Yes* och **[!UICONTROL Purchase Order]** = *Yes*.
1. Rensa konfigurationscachen.
1. Skapa ett nytt företag, aktivera det och aktivera *[!UICONTROL Purchase order]* för företaget.
1. Skapa en ny användare för företaget.
1. Skapa en *godkännanderegel* om du vill godkänna alla order på mer än *1 USD* av företagsadministratören.
1. Skapa ytterligare en källa.
1. Logga in som ny företagsanvändare.
1. Lägg två produkter i kundvagnen och gör en inköpsorder.
1. Inaktivera den andra produkten.
1. Logga in som företagsadministratör.
1. Öppna inköpsordern och se att inköpsordern innehåller båda produkterna och summan är för båda produkterna.
1. Godkänn inköpsordern.
1. Beställ.
1. Öppna orderinformationen.

<u>Förväntade resultat</u>:

* Det går inte att placera beställningen även om en produkt i beställningen är *inaktiverad* eller *inte i lager*.
* Knappen *[!UICONTROL Place Order]* är dold.

<u>Faktiska resultat</u>:

Den monterade ordern innehåller endast den första aktiva produkten, men ordersumman beräknas för båda produkterna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
