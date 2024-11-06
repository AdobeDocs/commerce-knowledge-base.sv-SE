---
title: 'MDVA-29400: Dubblettbeställningar som gjorts med PayPal Express Checkout'
description: MDVA-29400-korrigeringen löser problemet där dubblettbeställningar skapas när kunderna beställer med PayPal Express Checkout. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 är installerat. Korrigerings-ID är MDVA-29400. Observera att problemet har åtgärdats i Adobe Commerce 2.4.1.
exl-id: 75b943c8-5f7c-4d94-ae92-935428fdfcf8
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-29400: Dubblettbeställningar som gjorts med PayPal Express Checkout

MDVA-29400-korrigeringen löser problemet där dubblettbeställningar skapas när kunderna beställer med PayPal Express Checkout. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 har installerats. Korrigerings-ID är MDVA-29400. Observera att problemet har åtgärdats i Adobe Commerce 2.4.1.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Dubblettbeställningar skapas när användare gör beställningar med PayPal Express Checkout.

<u>Förutsättningar</u>:

Aktiverad och konfigurerad PayPal Express-utcheckning.

<u>Steg som ska återskapas</u>:

1. Lägg en produkt i kundvagnen.
1. Gå till utcheckningssidan och använd PayPal Express som betalningsmetod.
1. Det dirigeras om till betalande/express/review/ sida.
1. Montera order. Du omdirigeras till sidan Slutfört.
1. Gå tillbaka till PayPal/express/review/ Page.
1. Klicka på knappen **Montera ordning**.

<u>Förväntade resultat</u>:

Endast en order skapas.

<u>Faktiska resultat</u>:

Du får följande fel: *PayPal Express Checkout Token finns inte*, men den andra ordningen har placerats ut.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
