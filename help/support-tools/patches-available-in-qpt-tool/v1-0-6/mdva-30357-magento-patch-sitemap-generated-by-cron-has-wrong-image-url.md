---
title: 'MDVA-30357: platskartan som genereras av cron har fel bild-URL'
description: MDVA-30357-korrigeringen åtgärdar ett problem med fel bild-URL som skapas av en cron-genererad webbplatskarta i Commerce Admin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: c91f7ae0-0970-4918-9d1f-4ede6bfcb05f
feature: Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-30357: Webbplatskartan som genereras av cron har fel bild-URL

MDVA-30357-korrigeringen åtgärdar ett problem med fel bild-URL som skapas av en cron-genererad webbplatskarta i Commerce Admin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) 2.3.2 till 2.4.0

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Webbplatskartor som genereras av cron i Adobe Commerce innehåller fel bild-URL-sökväg.

<u>Steg som ska återskapas</u>:

1. I Commerce Admin skapar du en ny webbplats-, butik- eller butiksvy.
1. Lägg till minst en produkt i varje butik och lägg till minst en bild för varje produkt.
1. Aktivera **Platskarta genereras efter schema** i **Admin** > **Lagrar** > **Konfiguration** > **KATALOG** > **XML-platskarta** > **Genereringsinställningar**.
1. Generera en platskarta för någon av de två butikerna manuellt i **Admin** > **Marknadsföring** > **Platskarta** med ett platskartnamn som *sitemap.xml*.
   * Byt namn på filen till exempelvis *manual\_sitemap.xml* eller kopiera filinnehållet till valfri textredigerare.
1. Generera samma platskarta genom cron-jobb `sitemap_generate`.
1. Jämför den manuellt genererade platskartan *manual\_sitemap.xml* och platskartan som genereras av cron *sitemap.xml*.

<u>Förväntade resultat</u>:

URL:en för den cachelagrade platskartans bild är korrekt.

<u>Faktiska resultat</u>:

Den platskarta som genereras av cron innehåller fel bildsökvägs-URL. Om du försöker öppna bilden från *sitemap.xml* visas en standardplatshållare. Manuellt genererade URL:er för webbplatskartor påverkas inte av det här problemet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.

Mer information om webbplatskartor finns i följande artiklar i utvecklardokumentationen:

* [Lägg till webbplatskarta och sökrobotar](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [Konfigurera och kör cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [Säker cron.php för att köras i en webbläsare](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)
