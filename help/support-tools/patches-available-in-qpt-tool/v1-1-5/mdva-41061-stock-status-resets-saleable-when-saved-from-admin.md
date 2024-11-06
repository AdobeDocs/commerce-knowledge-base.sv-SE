---
title: 'MDVA-41061: Stock-status återställs till säljbar när produkten sparas från Admin'
description: MDVA-41061-korrigeringen åtgärdar ett problem där Stock-statusen återställs till säljbar när produkten sparas från administratören. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 är installerat. Korrigerings-ID är MDVA-41061. Den senaste patchversionen finns i QPT 1.1.15 med MDVA-41061-V3 patch-ID. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061: Stock-status återställs till säljbar när produkten sparas från Admin

MDVA-41061-korrigeringen åtgärdar ett problem där Stock-statusen återställs till säljbar när produkten sparas från administratören. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 har installerats. Korrigerings-ID är MDVA-41061. Den senaste patchversionen finns i QPT 1.1.15 med MDVA-41061-V3 patch-ID. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerstatus återställs till säljbar när produkten sparas från administratören.

<u>Förutsättningar</u>:

Lagermoduler är installerade.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt med kvantitet = 1.
1. Gör en beställning med den produkt som skapats i steg 1.
1. Kör cron - kontrollera att `inventory.reservations.updateSalabilityStatus`-kön har körts och att produktlagerstatusen har ändrats till noll i tabellen `cataloginventory_stock_status`.
1. Kontrollera produkten på frontend. Den ska markeras som **Utanför lager**.
1. Spara produkten i Admin utan ändringar.

<u>Förväntade resultat</u>:

* Lagerstatus ska inte uppdateras.
* Produkten ska ligga **utanför lagret** på frontend.

<u>Faktiska resultat</u>:

* Enkel produkt är markerad som **I Stock** på frontend.
* Användare får *Begärd kvantitet är inte tillgänglig*-meddelande när de försöker lägga till den i kundvagnen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
