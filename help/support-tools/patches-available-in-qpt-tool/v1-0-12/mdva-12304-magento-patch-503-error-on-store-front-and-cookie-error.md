---
title: 'MDVA-12304: 503-fel på store front and cookie error'
description: Denna MDVA-12304 Adobe Commerce-patch åtgärdar 503 fel på butiksskyltar med *Det går inte att skicka cookien. Maximalt antal cookies skulle överskridas.* felmeddelande i loggar. Detta är ett känt Adobe Commerce 2.2.5-problem. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 är installerat.
exl-id: b4b1a2f7-f328-488f-86b8-576b908792fb
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# MDVA-12304: 503-fel på butikens front och cookie-fel

Den här MDVA-12304 Adobe Commerce-korrigeringen åtgärdar 503 fel på butikshögarna och *Det går inte att skicka cookien. Maximalt antal cookies skulle överskridas.*-felmeddelande i loggar. Detta är ett känt Adobe Commerce 2.2.5-problem. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 är installerat.

## Berörda produkter och versioner

* **Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce lokal 2.2.5.
* **Kompatibel med Adobe Commerce-versioner:** Adobe Commerce (alla distributionsmetoder) 2.x.x.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunderna får 503 fel när de navigerar till butiken. I filen `var/log/exception.log` finns följande felmeddelande: *Det går inte att skicka cookien. Maximalt antal cookies skulle överskridas.*

Problemet inträffar eftersom Adobe Commerce standardgräns för cookies är 50, och om klientens webbläsare når gränsen genereras ett undantag i Commerce. Lösningen i plåstret ökar cookie-gränsen till 200.

<u>Steg att återskapa:</u>

503-felet kan visas när som helst när kunden försöker logga in och visa sin kundvagn.

I filen `var/log/exception.log` finns följande felmeddelande: *Det går inte att skicka cookien. Maximalt antal cookies skulle överskridas.*

<u>Faktiskt resultat:</u> Kunden kan inte kontrollera sin kundvagn eller slutföra sin beställning.

<u>Förväntat resultat:</u> Kunden kan kontrollera kundvagnen och slutföra sin beställning.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.


## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
