---
title: 'MDVA-38626: Administratörsanvändaren kan inte göra beställningar med PayPal Payflow Pro'
description: MDVA-38626-korrigeringen löser problemet där administratörsanvändaren inte kan lägga en order på backend med betalningsmetoden PayPal Payflow Pro. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 är installerat. Korrigerings-ID är MDVA-38626. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: b9257d42-d8df-4dd6-b2b4-70ddd6f3e414
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-38626: Administratörsanvändaren kan inte göra beställningar med PayPal Payflow Pro

MDVA-38626-korrigeringen löser problemet där administratörsanvändaren inte kan lägga en order på backend med betalningsmetoden PayPal Payflow Pro. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 har installerats. Korrigerings-ID är MDVA-38626. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren kan inte lägga order på backend-objektet med betalningsmetoden PayPal Payflow Pro.

<u>Steg som ska återskapas</u>:

1. Konfigurera betalningsmetoden PayPal Payflow Pro.
1. Gå till **Kunder** > **Alla kunder** och skapa ett kundkonto.
1. Klicka på **Skapa order**.
1. Lägg alla artiklar i vagnen.
1. Försök att lägga ordern med Payflow Pro.

<u>Förväntade resultat</u>:

Beställning placeras.

<u>Faktiska resultat</u>:

Användaren får 500 fel. Rapportloggen innehåller:

```
{"0":"No such entity with cartId = 0","1":"#1 Magento\\Quote\\Model\\QuoteRepository->loadQuote() called at [app\/code\/Magento\/Quote\/Model\/QuoteRepository.php:136]\n#2 Magento\\Quote\\Model\\QuoteRepository->get() called at [lib\/internal\/Magento\/Framework\/Interception\/Interceptor.php:58]\n#3 Mag
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
