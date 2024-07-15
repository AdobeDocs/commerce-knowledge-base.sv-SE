---
title: 'MDVA-30112: inkonsekvenser i stor numrering'
description: MDVA-30112-korrigeringen löser problemet där du har ett oväntat stort antal [reservationsinkonsekvenser](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) i tabellen "Inventering_reservation". Reservationsinkonsekvenser inkluderar oregistrerade öppna order och fullständiga order som inte är registrerade. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.2.
exl-id: db74fb61-dfeb-4e99-8513-d36fd68d2267
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# MDVA-30112: stora inkonsekvenser i antal reservationer

MDVA-30112-korrigeringen löser problemet där du oväntat har ett stort antal [reservationsinkonsekvenser](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) i tabellen `inventory_reservation`. Reservationsinkonsekvenser inkluderar oregistrerade öppna order och fullständiga order som inte är registrerade. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce om molninfrastruktur 2.3.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Värdet för [satsstorlek](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#list-inconsistencies-command) är värdet för hur många order som ska läsas in samtidigt. När det finns fler order än det här värdet anser Adobe Commerce att väntande order är inkonsekvenser.

>[!NOTE]
>
>Det finns en MDVA-33281-korrigering som åtgärdar tre andra problem med inkonsekventa lager. Detta inkluderar ett allvarligt PHP-fel när `bin/magento inventory:reservation:list-inconsistencies` körs i CLI. Ett annat problem som är åtgärdat är dubblettdata i inkonsekvenser-listan. Även frågan om när en reservation skapas före beställning (tidigare realisering baserad på reservation efter beställning). Information om lösningen finns i [MDVA-33281: problem med inventeringsinkonsekvenser](/help/support-tools/patches-available-in-qpt-tool/v1-0-14/mdva-33281-magento-patch-inventory-inconsistency-issues.md) i vår kunskapsbas för support.

<u>Förutsättningar</u>:

Du kör följande kommando i CLI för att visa reservationsinkonsekvenser i tabellen `inventory_reservation`:

```
magento inventory:reservation:list-inconsistencies
```

Ett oväntat stort antal reservationsinkonsekvenser visas och/eller kommandot slutförs aldrig.

<u>Steg som ska återskapas</u>:

1. Kör följande kommando i CLI för att lösa inkonsekvenser:

   ```
   bin/magento inventory:reservation:list-inconsistencies -r | bin/magento inventory:reservation:create-compensations
   ```

1. Beställ tre:
   * Tilldela varje enskild produkt.
   * Använd betalningsmetoden Check/Pengar Order så att orderstatusen blir &quot;väntande&quot;.
1. Du kan se tre poster med kvantiteten -1 i tabellen `inventory_reservation`. Kör följande kommando i CLI för att se eventuella inkonsekvenser:

   ```
   bin/magento inventory:reservation:list-inconsistencies
   ```

   Detta returnerar inga resultat, vilket är korrekt.

1. Kör följande kommando i CLI:

   ```
   Execute bin/magento inventory:reservation:list-inconsistencies      --bunch-size 1
   ```

   Statusorder för väntande visas som inkonsekvenser.

1. Kör följande kommando i CLI:

   ```
   bin/magento inventory:reservation:list-inconsistencies      -r --bunch-size 1 | bin/magento inventory:reservation:create-compensations
   ```

<u>Förväntade resultat</u>:

Adobe Commerce ska inte lösa inkonsekvenser i väntande statusorder. Inkonsekvenser i stockar bör lösas för order med status&quot;complete&quot;,&quot;closed&quot; och&quot;canceled&quot;.

<u>Faktiska resultat</u>:

När det finns beställningar som är större än det angivna värdet för buntstorlek, betraktar Adobe Commerce beställningar med &quot;väntande&quot; status som inkonsekvenser och lägger till flera poster med inkonsekvent matchning för samma beställning.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
