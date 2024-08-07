---
title: "MDVA-23426 Magento patch: emails sent as attachments from Outlook"
description: Korrigeringen MDVA-23426 Magento åtgärdar ett problem där e-postmeddelanden skickas som bilagor från Magento från MS Outlook. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 är installerat. Observera att problemet löstes i Magento 2.3.5.
exl-id: 0b4c3e33-76c5-48b0-b1a8-a967cea11b98
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# MDVA-23426 Magento-patch: e-postmeddelanden som skickas som bilagor från Outlook

Korrigeringen MDVA-23426 Magento åtgärdar ett problem där e-postmeddelanden skickas som bilagor från Magento från MS Outlook. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 är installerat. Observera att problemet löstes i Magento 2.3.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Magento-version:** Magento Commerce Cloud 2.3.3.

**Kompatibel med Magento-versioner:** Magento Commerce och Magento Commerce Cloud 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

E-postmeddelanden tas emot med en tom brödtext och innehållet inkluderas som en bifogad fil.

<u>Förutsättningar:</u> Outlook/Exchange används som klient/server-kombination.

<u>Steg som ska återges:</u> 1. Skicka en beställning, beställningsmeddelandet eller leveransmeddelandet skickas.2. E-postmeddelandet tas emot.

<u>Faktiskt resultat:</u> E-postmeddelandet visas med en tom brödtext och innehållet inkluderas som en ATT\*-märkt bifogad fil i e-postmeddelandet. <u>Förväntat resultat:</u>

E-postmeddelandet tas emot utan någon bifogad fil och e-postmeddelandets brödtext innehåller innehållet.

## Tillämpa korrigeringen

Instruktioner om hur du använder en QPT-korrigering finns på följande länkar beroende på din Magento-produkt:

* Magento Commerce: DevDocs [Tillämpa korrigeringar med verktyget för kvalitetspatchar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud: DevDocs [Upgrades and Patches > Apply patches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget Kvalitetspatchar släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Leta efter Magento-problem med verktyget för kvalitetspatchar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
