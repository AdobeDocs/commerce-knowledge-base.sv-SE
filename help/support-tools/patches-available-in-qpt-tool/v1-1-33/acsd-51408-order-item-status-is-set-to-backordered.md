---
title: 'ACSD-51408: Orderobjektets status är felaktigt inställd på [!UICONTROL backordered]'
description: Använd ACSD-51408-korrigeringen för att åtgärda Adobe Commerce-problemet där orderobjektets status felaktigt är inställd på [!UICONTROL backordered].
feature: B2B, Orders
role: Admin
exl-id: 0355beca-4612-438f-8f91-be42d8d637e9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# ACSD-51408: Orderobjektets status är felaktigt inställd på *[!UICONTROL backordered]*

ACSD-51408-korrigeringen åtgärdar ett problem där orderartikelns status är felaktigt inställd på [!UICONTROL backordered]. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 har installerats. Korrigerings-ID är ACSD-51408. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Orderobjektets status är felaktigt inställd på *[!UICONTROL backordered]*.

<u>Förutsättningar</u>:

Adobe Commerce B2B- och Inventory management-moduler (MSI) är installerade.

<u>Steg som ska återskapas</u>:

1. Skapa en ny webbplats, butik och butiksvy.
1. Skapa en ny källa.
1. Skapa ett nytt arkiv som är länkat till den nya webbplatsen som skapades i steg 1 och tilldela källan som skapades i steg 2.
1. Skapa ett företag och tilldela det till den nya webbplatsen som skapas i steg 1.
1. Skapa en ny kund och tilldela den till företaget som skapats i steg 4.
1. Skapa en produkt, tilldela den till den nya webbplatsen och ange **[!UICONTROL default stock]** = *0* och **[!UICONTROL new stock]** till större än *0*.
1. Aktivera **[!UICONTROL backorders]**.
1. Aktivera betalningsmetoden **[!UICONTROL Check/Money Order]** för det nya webbplatsomfånget.
1. Aktivera **[!UICONTROL Flat Rate shipping method]** för nytt webbplatsomfång.
1. Skapa en ny order från **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. Välj den nya kunden som skapades i steg 5.
1. Välj den nya butik som skapades i steg 1.
1. Välj den produkt som skapades i steg 6.
1. Fyll i orderinformationen, inklusive betalnings- och leveransmetoder.
1. Skicka ordern.
1. Kontrollera *objektstatus*.

<u>Förväntade resultat</u>

Artikeln är tillgänglig för leverans från lagret. Objektstatusen är *[!UICONTROL ordered]*.

<u>Faktiska resultat</u>

Objektstatusen är *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[Status för orderartikel är felaktigt inställd på *[!UICONTROL Ordered]* när produktbeställningen är 0.](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
