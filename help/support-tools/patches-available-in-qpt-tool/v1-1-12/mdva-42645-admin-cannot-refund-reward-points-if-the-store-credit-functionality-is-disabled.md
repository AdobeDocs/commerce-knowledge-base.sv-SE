---
title: "MDVA-42645: Administratören kan inte återbetala belöningspoäng för inaktiverad butikskredit"
description: MDVA-42645-korrigeringen löser problemet där administratören inte kan återbetala belöningspoäng om butikskreditfunktionen är inaktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-42645. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 8e8f8c07-c1a2-4031-a2fb-cb737165dc2c
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-42645: Administratören kan inte återbetala belöningspoäng för inaktiverade butikskrediter

MDVA-42645-korrigeringen löser problemet där administratören inte kan återbetala belöningspoäng om butikskreditfunktionen är inaktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-42645. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratören kan inte återbetala belöningspoäng om butikskreditfunktionen är inaktiverad.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Skapa ett nytt kundkonto och lägg till några belöningspoäng.
1. Inaktivera butikskreditfunktionen genom att gå till **Store** > Inställningar > **Konfiguration** > **Kund** > **Kundkonfiguration** > **Butikskreditalternativ**.
1. Logga in som den kund som belöningspoängen tilldelas.
1. Lägg en produkt i kundvagnen och navigera till kassan.
1. Använd belöningspoängen i betalningsavsnittet och placera ordern.
1. Öppna ordern i administratören och fakturera ordern.
1. Klicka på länken **Kreditnota** för att skapa en ny kreditnota.
1. Markera alternativet Återbetala räntepunkter längst ned och klicka på **Återbetala offline**.

<u>Förväntade resultat</u>:

* Kreditnotan har skapats.
* Returpunkterna återbetalas utan problem.

<u>Faktiska resultat</u>:

Du får följande felmeddelande: *Du kan inte använda mer butikskrediter än orderbeloppet.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
