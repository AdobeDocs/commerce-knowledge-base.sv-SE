---
title: 'MDVA-31759-korrigering: CSV-import ignorerar attributuppdateringar'
description: MDVA-31759-korrigeringen åtgärdar ett problem där CSV-import ignorerar ytterligare attribut med typerna *Dropdown* och *Text Area*. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 5426866c-893f-4abe-bfbc-6e7b30dd8dab
feature: Attributes, Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-31759-korrigering: CSV-import ignorerar attributuppdateringar

Korrigeringen MDVA-31759 åtgärdar ett problem där CSV-import ignorerar ytterligare attribut med typerna *Listruta* och *Textområde*. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.4.0

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

CSV-import ignorerar ytterligare attribut med typerna *Listruta* och *Textområde*.

<u>Steg som ska återskapas</u>:

1. Logga in på Commerce Admin.
1. Skapa ett produktattribut med följande konfiguration:
   * **Standardetikett**: *G003*
   * **Katalogindatatyp för butiksägare**: *Textområde* eller *Listruta*
   * **Attributkod**: *G003*
   * **Omfång**: *Global*
1. Lägg till ovanstående attribut i standardattributuppsättningen.
1. Skapa en produkt med standardattributuppsättningen och ange ett värde för det nya attributet.
1. Exportera produkten till CSV.
1. Uppdatera attributvärdet i kolumnen **additional\_attributes**.
1. Importera den uppdaterade CSV-filen.

<u>Förväntade resultat</u>:

G003-attributvärdet uppdateras.

<u>Faktiska resultat</u>:

G003-attributvärdet uppdateras inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [korrigeringsfilerna i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
