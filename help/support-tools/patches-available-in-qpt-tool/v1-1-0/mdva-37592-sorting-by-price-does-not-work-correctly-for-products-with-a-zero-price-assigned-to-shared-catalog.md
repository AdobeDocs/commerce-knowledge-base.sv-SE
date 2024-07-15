---
title: 'MDVA-37592: Sortering efter pris fungerar inte för produkter med priset noll'
description: MDVA-37592 Adobe Commerce-korrigeringen löser problemet där sortering efter pris inte fungerar korrekt för produkter med priset noll som tilldelats en delad katalog. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 är installerat. Patch-ID:t är MDVA-37592. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592: Sortering efter pris fungerar inte för produkter med priset noll

MDVA-37592 Adobe Commerce-korrigeringen löser problemet där sortering efter pris inte fungerar korrekt för produkter med priset noll som tilldelats en delad katalog. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 har installerats. Patch-ID:t är MDVA-37592. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce i vår molnarkitektur 2.4.0-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionstyper) 2.3.6-2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sortering efter pris fungerar inte korrekt för produkter med priset noll tilldelat till en delad katalog.

<u>Förutsättningar</u>:

B2B är installerat.

<u>Steg som ska återskapas</u>:

1. Aktivera delad katalog.
1. Skapa fyra produkter med följande priser och tilldela dem till en kategori - 50, 60, 70 och 80 dollar.
1. Skapa en delad katalog med produkterna ovan.
1. Ställ in det anpassade priset på noll för produkten med priset 70 USD.
1. Skapa nu en företagsanvändare och tilldela den till den delade katalog som just har skapats.
1. Logga in med företagskontot och bläddra till den kategori där produkterna är tilldelade.
1. Försök sortera efter pris.

<u>Förväntade resultat</u>:

Produkten med priset noll är korrekt sorterad.

<u>Faktiska resultat</u>:

Produkten med priset noll är INTE korrekt sorterad. I stället sorteras den efter det ursprungliga priset.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

* Adobe Commerce lokalt: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i vår molnarkitektur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
