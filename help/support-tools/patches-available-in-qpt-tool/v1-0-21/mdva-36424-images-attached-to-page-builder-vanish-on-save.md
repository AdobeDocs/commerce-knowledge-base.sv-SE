---
title: 'MDVA-36424: Bilder som är kopplade till Page Builder försvinner när de sparas'
description: Korrigeringen MDVA-36424 löser problemet där bilderna som är kopplade till sidbyggarelement försvinner när kategorin sparas för andra gången för flera webbplatser, där standardwebbplatsens bas-URL är en annan än admin-URL:en. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Korrigerings-ID är MDVA-36424. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: ae15db2d-0d9f-48c1-87e4-61da1558a57c
feature: Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-36424: Bilder som är kopplade till Page Builder försvinner när de sparas

Korrigeringen MDVA-36424 löser problemet där bilderna som är kopplade till sidbyggarelement försvinner när kategorin sparas för andra gången för flera webbplatser, där standardwebbplatsens bas-URL är en annan än admin-URL:en. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Korrigerings-ID är MDVA-36424. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.6

**Kompatibel med Magento-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.5 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Mediebilder som är kopplade till sidbyggarelement sparas inte om backend-bas-URL:en inte är samma som storefront-URL:en.

<u>Steg som ska återskapas</u>:

1. Skapa en andra webbplats - webbplats2.
1. Ange en annan bas-URL för webbplats2 (den bas-URL som används i admin ska vara en annan än den andra webbplatsen).
1. Ange den andra webbplatsen som standardwebbplats (**Lagrar** > *Inställningar* > **Alla butiker** > Välj den andra webbplatsen > Ange som *standard*).
1. Gå till kategorisidan i serverdelen och gå till en kategoriredigeringsvy.
1. Navigera till **Innehåll** > *Beskrivning*.
1. Lägg till en kolumn i innehållet och ange en bakgrundsbild med mediegalleriet.
1. Spara kategorin.
1. Gå till **Innehåll** > *Beskrivning* igen. Den sparade bilden visas korrekt.
1. Spara kategorin igen.
1. Gå till **Innehåll** > *Beskrivning*.

<u>Förväntade resultat</u>:

Bilden tas inte bort när du sparar kategorin.

<u>Faktiska resultat</u>:

Bilden tas bort när du har sparat kategorin en andra gång.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
