---
title: 'MDVA-33281 patch: problem med inkonsekventa lager'
description: MDVA-33281-korrigeringen åtgärdar tre problem med inkonsekventa lager. Klicka på de länkade problemen under avsnittet Problem för att se hur du återger felen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 är installerat.
exl-id: adba9728-6e42-467e-943d-cf8af0bec353
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-33281-korrigering: problem med inkonsekventa lager

MDVA-33281-korrigeringen åtgärdar tre problem med inkonsekventa lager. Klicka på de länkade problemen under avsnittet Problem för att se hur du återger felen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 är installerat.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.5-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce om molninfrastruktur 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Korrigeringen åtgärdar inkonsekventa lagerproblem som:

* **Allvarligt PHP-fel** uppstod när `bin/magento inventory:reservation:list-inconsistencies` kördes i CLI på grund av fel SKU-parametertyp.
* **Duplicera data** i inkonsekvent lista.
* **Ny reservation** kommer att skapas före beställning (tidigare realisering baserad på reservation efter beställning). Om det finns fel i orderplaceringen läggs ytterligare reservation till för att kompensera.

>[!NOTE]
>
>Det finns också en MDVA-30112-korrigering som löser problemet där det finns ett oväntat stort antal [reservationsinkonsekvenser](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) i utvecklardokumentationen i tabellen `inventory_reservation`. Information om lösningen finns i [MDVA-30112 Magento-korrigering: stor inkonsekvens för talreservation](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md) i vår kunskapsbas för support.

## Allvarligt PHP-fel

<u>Steg som ska återskapas</u>:

Allvarligt PHP-fel vid körning av `bin/magento inventory:reservation:list-inconsistencies`.

Om du vill visa en lista över reservationsinkonsekvenser loggar du in på produktionsservern och kör följande kommando i CLI (-r switch - raw output):

<pre>bin/magento-lager:reservation:list-inconsistent -r</pre>

<u>Förväntade resultat</u>:

Listan över reservationsinkonsekvenser skapas. De returneras i följande format:

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>Faktiska resultat</u>:

Allvarligt PHP-fel har returnerats.

## Duplicera data

Dubblettdata finns i `inventory_reservation table`.

<u>Steg som ska återskapas</u>:

Om du vill felsöka reservationsinkonsekvenser kör du följande kommando:

<pre>VÄLJ *, COUNT(*)
FRÅN lager_reservation
GROUP BY-metadata, sku, kvantitet
MED COUNT(*) &gt; 1</pre>

<u>Förväntade resultat</u>:

Inga dubbletter.

<u>Faktiska resultat</u>:

Det finns dubbletter.

## Ny reservation

<u>Steg som ska återskapas</u>:

Ny reservation skapad före beställning placerad:

1. Importera databasen.
1. Kör `bin/magento setup:upgrade` i terminalen.
1. Visa inkonsekvenser genom att köra `bin/magento inventory:reservation:list-inconsistencies        -i -r` i terminalen.

<u>Förväntade resultat</u>:

Ingen slinga och mycket snabbare resultat.

<u>Faktiska resultat</u>:

Samma resultat visas i en oändlig slinga, eller så misslyckas kommandot med `memory_limit`, beroende på systeminställningarna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [korrigeringsfilerna i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
