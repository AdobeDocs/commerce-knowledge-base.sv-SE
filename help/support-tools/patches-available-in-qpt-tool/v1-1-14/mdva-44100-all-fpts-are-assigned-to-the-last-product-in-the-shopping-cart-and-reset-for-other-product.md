---
title: "MDVA-44100: Alla bildrutefrekvenser tilldelas den sista produkten i kundvagnen"
description: MDVA-44100-korrigeringen löser problemet där alla bildrutefrekvenser tilldelas den sista produkten i kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Korrigerings-ID är MDVA-44100. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: ab0f195c-fcc6-41ac-932d-d2603d068aa6
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-44100: Alla bildrutefrekvenser tilldelas den sista produkten i kundvagnen

MDVA-44100-korrigeringen löser problemet där alla bildrutefrekvenser tilldelas den sista produkten i kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Korrigerings-ID är MDVA-44100. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Alla bildrutefrekvenser tilldelas den sista produkten i kundvagnen och FPT-värdena för resten av produkterna återställs.

<u>Steg som ska återskapas</u>:

1. Gå till **Store** > **Configuration** > **Sales** > **Tax** och ange:
   * Aktivera FPT = Ja
   * Tillämpa skatt på FPT = Ja
   * Inkludera FPT i delsumma = Ja
1. Gå till **Lagrar** > **Attribut** > **Produkt** och skapa ett nytt attribut med typen = Fast produktskatt.
1. Lägg till attributet i en attributuppsättning.
1. Skapa två produkter från attributuppsättningen och konfigurera FPT-attributet för ditt land och din stat.
1. Lägg till båda objekten i ordern.
1. Ange en adress som kräver att FPT betalas.
1. Beställ.
1. Kontrollera objektlistan i ordern.

<u>Förväntade resultat</u>:

FPT visas under varje produkt.

<u>Faktiska resultat</u>:

FPT-värdena från båda objekten visas under det andra objektet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
