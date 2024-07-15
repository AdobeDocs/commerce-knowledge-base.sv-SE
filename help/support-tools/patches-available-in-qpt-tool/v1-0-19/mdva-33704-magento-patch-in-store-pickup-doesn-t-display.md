---
title: "MDVA-33704-korrigering: Butiksupphämtning visas inte"
description: MDVA-33704-korrigeringen åtgärdar ett problem där produkter med alternativ för hämtning i butik inte visas som leveranssätt.
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-33704-korrigering: Butiksupphämtning visas inte

MDVA-33704-korrigeringen åtgärdar ett problem där produkter med alternativ för hämtning i butik inte visas som leveranssätt.

Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-33704. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.4.0-p1

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.4.0-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättning</u>:<br>

**Plockning i butik** har aktiverats

<u>Steg som ska återskapas</u>:

1. Lägg en produkt i kundvagnen.
1. Gå till kassan.
1. Lägg till leveransinformation och välj en annan leveransmetod än att hämta i butiken.
1. Välj **Fortsätt till betalning**, men fortsätt inte till betalningssidan.
1. Gå istället tillbaka till avsnittet **Kontakt och leverans**.
1. Välj **Hämta**.
1. Välj **Store** och **Klicka för betalning**.
1. Observera att din leveransadress automatiskt anges som faktureringsadress.
1. Uppdatera webbsidan.

<u>Förväntade resultat</u>:

Upphämtningsalternativet i butiken visas som en leveransmetod, som förväntat.

<u>Faktiska resultat</u>:

Alternativet för hämtning i butik visas inte som en leveransmetod.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
