---
title: 'MDVA-43726: Katalogprisregeln kan inte tillämpas efter partiell omindexering'
description: MDVA-43726-korrigeringen åtgärdar ett problem där katalogprisregeln som baseras på butiksattributmatchning inte kan tillämpas efter partiell omindexering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-43726. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 70e7e1d2-e601-4fed-9274-a1a619de29e1
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-43726: Katalogprisregeln kan inte tillämpas efter partiell omindexering

MDVA-43726-korrigeringen åtgärdar ett problem där katalogprisregeln som baseras på butiksattributmatchning inte kan tillämpas efter partiell omindexering. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-43726. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Katalogprisregeln som baseras på matchning av butiksattribut kan inte tillämpas efter partiell omindexering.

<u>Steg som ska återskapas</u>:

1. Ställ in indexeringsläget så att det körs enligt schema.
1. Skapa två konfigurerbara produktattribut. Exempel: Färg (visuell färgruta) och Storlek (färgruta).
1. Skapa en konfigurerbar produkt med båda attributen som skapas i steg 2.
1. När du har skapat produkterna skapar du en **Ja/Nej** type-attribut och gör det synligt i regelvillkoren.
1. Lägg till det här attributet i standardattributuppsättningen.
1. Skapa en katalogprisregel som ska användas när det här attributet är inställt på **Ja**.
1. Öppna en av de enkla produkterna som hör till den konfigurerbara produkten.
1. Ändra omfattningen för att lagra vyn och uppdatera attributvärdet till **Ja**.
1. Kör `CRON` och kontrollera priset på frontend.
1. Kör en fullständig omindexering. Kontrollera priset på fronten igen.
1. Uppdatera den konfigurerbara produktkategorin.
1. Kör `CRON` och kontrollera priset igen på frontend.

<u>Förväntade resultat</u>:

Katalogregeln tillämpas korrekt utan en fullständig omindexering med inkrementella indexerare.

<u>Faktiska resultat</u>:

Katalogregeln gäller inte utan att du behöver köra ett fullständigt omindex.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
