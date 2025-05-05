---
title: 'MDVA-31763: Katalogens prisregler återställs tills manuell omindexering utförs'
description: MDVA-31763-korrigeringen löser problemet där katalogprisreglerna återställs tills manuell omindexering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 är installerat. Patch-ID:t är MDVA-31763. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: eb2dfd1a-6d12-4676-82c1-bf92c6fa9fda
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-31763: Katalogens prisregler återställs tills manuell omindexering utförs

MDVA-31763-korrigeringen löser problemet där katalogprisreglerna återställs tills manuell omindexering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 har installerats. Patch-ID:t är MDVA-31763. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När `catalogrule_product` partiell indexerare körs på konfigurerbara produkter försvinner katalogreglerna.

<u>Steg som ska återskapas</u>:

1. Logga in på Admin Backend.
1. Gå till **Lagrar** > **Attribut** > **Produkt** och sök efter attributet &quot;tillverkare&quot;.
   * Lägg till några alternativ och ange *Ja* som Använd för kampanjregelvillkor.
1. Gå till **Lagrar** > **Attribut** > **Attributuppsättningar**.
   * Välj standardattributuppsättningen och lägg till attributet &quot;manufacturer&quot; i den.
1. Skapa en konfigurerbar produkt med några varianter.
1. Ange attributvärdet &quot;manufacturer&quot; för en tidigare skapad konfigurerbar produkt.
1. Skapa katalogregler:
   * Aktiv = Ja
   * Webbplatser = huvudwebbplats
   * Kundgrupper = INTE INLOGGAD
   * Villkor: tillverkare = \&lt;valt värde för konfigurerbar produkt>
   * Åtgärder: Alla rabatter
1. Gör ett fullständigt index.
1. Kontrollera produktpriset på PDP och se till att priset är korrekt.
1. Uppdatera viktattributet för den skapade konfigurerbara produkten.
1. Kontrollera produktpriset på PDP.

<u>Förväntade resultat</u>:

Katalogprisreglerna som har angetts för konfigurerbara produkter tas inte bort under partiell omindexering.

<u>Faktiska resultat</u>:

Katalogens prisregler för konfigurerbara produkter försvinner vid partiell omindexering.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
