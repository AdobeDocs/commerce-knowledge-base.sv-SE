---
title: 'MDVA-36833: trasig sidnumrering på sökresultatsidan'
description: Korrigeringen MDVA-36833 åtgärdar ett problem där sidnumrering bryts när den delade katalogen är aktiverad och vissa produkter har undantagits från den delade katalogen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 är installerat. Patch-ID:t är MDVA-36833. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 7105c4ed-48d9-4d4c-bf12-5914bbad62da
feature: Catalog Management, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-36833: bruten sidnumrering på sökresultatsidan

Korrigeringen MDVA-36833 åtgärdar ett problem där sidnumrering bryts när den delade katalogen är aktiverad och vissa produkter har undantagits från den delade katalogen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 är installerat. Patch-ID:t är MDVA-36833. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce (alla distributionsmetoder) 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du utesluter vissa produkter från en delad katalog kan det leda till en bruten sidnumrering för sökresultaten.

<u>Steg att återskapa:</u>

1. Aktivera delad katalog.
1. Gå till **Katalog** > **Delade kataloger** och konfigurera standardkatalogen för delad katalog genom att tilldela alla produkter till den.
1. Läs in butiken och sök efter&quot;jacka&quot;.
1. Observera de produkter som listas på första sidan. Det ska finnas tolv produkter.
1. Anteckna 11 SKU:er på den första sidan. Gå till serverdelen och läs in standardkatalog för delad katalog.
1. Ta bort tilldelning av tidigare angivna SKU:er från standardkatalogen för delad katalog.
1. Gå till butiken och sök efter &quot;jacka&quot;.
1. Kontrollera den första sidan i sökresultaten.

<u>Faktiskt resultat:</u>

Den första sidan innehåller en produkt och resten av produkterna finns på den andra sidan.

<u>Förväntat resultat:</u>

Den första sidan ska innehålla 12 produkter.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.


## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
