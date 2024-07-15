---
title: 'MDVA-30815: Elasticsearch tomma sökresultat'
description: Korrigeringen MDVA-30815 åtgärdar ett problem där Elasticsearch visar en tom sida när sökresultatens begränsningsalternativ ändras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.3.5.
exl-id: dbe41a43-e248-407e-8cf9-319ad5843935
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30815: Elasticsearch tomma sökresultat

Korrigeringen MDVA-30815 åtgärdar ett problem där Elasticsearch visar en tom sida när sökresultatens begränsningsalternativ ändras. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.3.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce i molninfrastruktur 2.3.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du ändrar sökresultatens begränsningsalternativ när du använder Elasticsearch visas en tom sida.

<u>Förutsättningar</u>:

Elasticsearch är **aktiverat**. Gå till **STORES** > **Inställningar** > **Konfiguration** > **Katalog** > **Katalogsökning**.

<u>Steg som ska återskapas</u>:

1. Gå till din webbplats.
1. Sök efter en produkt i huvudsökfältet.
1. När sökresultatsidorna visas klickar du på den sista sidan i sökresultatsidorna.
1. Välj **Visa xx per sida** från begränsningsalternativet. Kontrollera att det här är en annan gräns för antal sökresultat än den som är konfigurerad för tillfället.

<u>Förväntade resultat</u>:

På sidan visas det konfigurerade antalet produktresultat.

<u>Faktiska resultat</u>:

Tom sida visas. Det här felet kan också visas i `var/report` : *\`&quot;0&quot;:&quot;SQLSTATE\[42000\]: Syntaxfel eller åtkomstfel: 1064 Du har ett fel i SQL-syntaxen. Kontrollera i handboken som motsvarar MySQL-serverversionen om du vill ha rätt syntax nära&quot;\&quot;*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
