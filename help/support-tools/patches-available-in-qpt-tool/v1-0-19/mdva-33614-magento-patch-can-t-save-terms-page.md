---
title: "MDVA-33614-korrigering: det går inte att spara sidan Terms"
description: "MDVA-33614-korrigeringen åtgärdar ett problem där det inte går att spara redigeringar på Terms-sidan eftersom Page Builder genererar följande fel: *Ett fel uppstod när Page Builder startades. Kontakta din tekniska supportkontakt*. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Korrigerings-ID är MDVA-33614. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2."
exl-id: d9b287bb-eab4-4c33-b725-ae0074962447
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-33614-korrigering: Det går inte att spara sidan Terms

MDVA-33614-korrigeringen åtgärdar ett problem där det inte går att spara redigeringar på villkorssidan eftersom Page Builder genererar följande fel: *Ett fel uppstod när Page Builder startades. Kontakta din tekniska supportkontakt*. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Korrigerings-ID är MDVA-33614. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce lokalt och Adobe Commerce i molninfrastruktur 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att spara redigeringar på sidan Termer eftersom Page Builder genererar ett fel.

<u>Steg som ska återskapas</u>:

1. Gå till **CONTENT** > Elements > **Pages** i Commerce Admin.
1. Välj sidan Termer.
1. Klicka på **Redigera**.
1. Gör en redigering och klicka på **Spara**.

<u>Förväntat resultat</u>:

Sidan sparas utan fel.

<u>Faktiskt resultat</u>:

Följande fel visas: *Ett fel uppstod när Page Builder startades. Kontakta din tekniska supportkontakt*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
