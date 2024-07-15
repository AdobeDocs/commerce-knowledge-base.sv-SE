---
title: 'MDVA-39229: Fel efter uppdatering av starttid för katalogregel Mellanlagringsuppdatering'
description: MDVA-39229-korrigeringen åtgärdar ett problem där användare får ett felmeddelande efter att starttiden för uppdateringen av katalogregelns mellanlagring har uppdaterats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 är installerat. Korrigerings-ID är MDVA-39229. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229: Fel efter uppdatering av starttid för katalogregel Mellanlagringsuppdatering

MDVA-39229-korrigeringen åtgärdar ett problem där användare får ett felmeddelande efter att starttiden för uppdateringen av katalogregelns mellanlagring har uppdaterats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 har installerats. Korrigerings-ID är MDVA-39229. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.3.4-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användarna får ett fel efter att starttiden för uppdateringen av katalogregelns mellanlagring har uppdaterats.

<u>Steg som ska återskapas</u>:

1. Skapa en katalogprisregel.
1. Skapa och kör alla mellanlagringsuppdateringar.
1. Kör frågan och verifiera att flaggan Förproduktion skapades.


   `select * from flag;`


1. Skapa en ny mellanlagringsuppdatering som börjar efter fem minuter.
1. Öppna **Innehåll** > **Förproduktion** > **Kontrollpanel** > **Ny uppdatering** och fördröj starttiden med en minut.
1. Vänta i sex minuter.
1. Spring cron.

<u>Förväntade resultat</u>:

Uppdateringens starttid ändras och uppdateringen tillämpas. Den gamla uppdateringen tas bort från tabellen `staging_update`.

<u>Faktiska resultat</u>:

Användarna får följande fel:

*report.ERROR: Cron Job staging_synchronize_entities_period har ett fel: Det går inte att ta bort den aktiva uppdateringen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
