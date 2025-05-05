---
title: 'ACSD-49464: Fakturor, leveranser och kreditnotor har inte flyttats tillbaka från arkivet'
description: Använd patchen ACSD-49464 för att åtgärda Adobe Commerce-problemet där fakturor, leveranser och kreditnotor inte flyttas tillbaka från arkivet när orderId är annorlunda.
exl-id: 845f9878-5f7e-4e58-8f8a-b02af17b3f11
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-49464: Fakturor, leveranser och kreditnotor har inte flyttats tillbaka från arkivet

Korrigeringen ACSD-49464 åtgärdar ett problem där fakturor, leveranser och kreditnotor inte flyttas tillbaka från arkivet när orderId är annorlunda. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 har installerats. Korrigerings-ID är ACSD-49464. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Fakturor, leveranser och kreditnotor flyttas inte tillbaka från arkivet när orderId är annorlunda.

<u>Steg som ska återskapas</u>:

1. Möjliggör arkivering av order, fakturor, leveranser och kreditnotor.
1. Skapa och slutför en beställning, inklusive frakt, faktura och kreditnota.
1. Kontrollera att ID:n för frakt, faktura och kreditnota inte är samma som ordernumret.
1. Flytta ordningen för arkivering.
1. Återställ den arkiverade ordern till orderhantering.
1. Kontrollera information om faktura, frakt och kreditnota under respektive [!UICONTROL Invoice]-, [!UICONTROL Shipping]- och [!UICONTROL Credit Memo]-rutnätssida.

<u>Förväntade resultat</u>:

De ursprungliga relaterade posterna återställs när ordningen flyttas från arkivlistan till orderhantering.

<u>Faktiska resultat</u>:

* Inga poster för frakt-, faktura- och kreditnotor om alla ID:n är olika.
* Om order och relaterade poster har samma ID returneras posterna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
