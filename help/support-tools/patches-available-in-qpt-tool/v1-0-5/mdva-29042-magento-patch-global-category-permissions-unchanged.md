---
title: 'MDVA-29042: global kategoribehörighet oförändrad'
description: MDVA-29042-korrigeringen åtgärdar ett problem där katalogbehörigheterna ändrades till "*Tillåt*" automatiskt efter att en ny produkt har lagts till i den delade katalogen i Commerce Admin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat. Observera att problemet korrigerades i Adobe Commerce 2.3.6 med B2B-tillägget.
exl-id: 491b8881-87ec-4820-8f87-54961682e961
feature: Catalog Management, Categories, Customer Service, Roles/Permissions
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29042: oförändrade globala kategoribehörigheter

MDVA-29042-korrigeringen åtgärdar ett problem där katalogbehörigheter ändrades till *Tillåt* automatiskt efter att en ny produkt har lagts till i den delade katalogen i Commerce Admin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat. Observera att problemet korrigerades i Adobe Commerce 2.3.6 med B2B-tillägget.

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.3.3 till 2.3.4-p2 med B2B-tillägg

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du avmarkerar en kundgrupp från de globala kategoribehörigheterna i Commerce Admin anges inte den kundgruppen automatiskt till *Neka* inom kategoribehörigheter.

<u>Förutsättningar</u>:

* B2B-instans med en kundgrupp definierad och markerad under **STORES** > **Configuration** > **CATALOG** > **Catalog** > **kategoribehörigheter** för:
   * **Tillåt bläddringskategori**
   * **Visa produktpriser**
   * **Tillåt tillägg i kundvagnen**
* Under varje **kategori** definieras kundgruppen som *Tillåt* för:
   * **Bläddringskategori**
   * **Visa produktpriser**
   * **Lägg i kundvagnen**

<u>Steg som ska återskapas</u>:

1. Gå till **STORES** > **Konfiguration** > **KATALOG** > **Katalog** > **Kategoribehörigheter** och avmarkera kundgruppen från:
   * **Tillåt bläddringskategori**
   * **Visa produktpriser**
   * **Tillåt tillägg i kundvagnen**
1. Klicka på knappen **Spara konfiguration**.
1. Vänta på att indexerarna ska köras.
1. Titta på **KATALOG** > **Kategorier** > **Kategoribehörigheter**.

<u>Förväntade resultat</u>:

**Kategoribehörigheter** anges till *Neka* för alla kategorier för kundgruppen.

<u>Faktiska resultat</u>:

Ingen ändring av kategoribehörigheter för kundgruppen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.

Mer information om funktioner för B2B-företag finns i följande artiklar i utvecklardokumentationen:

* [Utvecklarhandbok för B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Hantera företagsroller](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Konfigurationssökvägar för Adobe Commerce Enterprise B2B-tillägg ](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
