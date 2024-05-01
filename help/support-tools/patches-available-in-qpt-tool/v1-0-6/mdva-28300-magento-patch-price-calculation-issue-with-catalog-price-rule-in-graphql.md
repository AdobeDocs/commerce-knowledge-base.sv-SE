---
title: 'MDVA-28300: prisberäkningsproblem med katalogprisregel i GraphQL'
description: MDVA-28300-korrigeringen åtgärdar ett problem där GraphQL-begäran inte återspeglar prisändringar i katalogens prisregler. Den här korrigeringen är tillgänglig när QPT (Quality Patches Tool) v.1.0.6 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.3.6.
exl-id: 86079d29-db69-4758-a159-aeed8e0ea21f
feature: Catalog Management, GraphQL, Customer Service, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# MDVA-28300: Prisberäkningsproblem med katalogprisregel i GraphQL

>[!WARNING]
>
>En ny patch som heter MDVA-33975 åtgärdar GraphQL problem med prisberäkning. MDVA-28300 skrivs av och du bör använda MDVA-33975-patchen. Om du vill komma åt den här korrigeringen läser du [MDVA-33975: GraphQL prisberäkningar](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

MDVA-28300-korrigeringen åtgärdar ett problem där GraphQL-begäran inte återspeglar prisändringar i katalogens prisregler. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.3.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce lokal 2.3.5-p1

**Kompatibel med Adobe Commerce:** Adobe Commerce On Premises och Adobe Commerce om molninfrastruktur 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När en katalogprisregel tillämpas på en viss kundgrupp, beräknas artikelpriserna i kundvagnen och ordersumman inte korrekt i GraphQL.

<u>Steg som ska återskapas:</u>

1. Skapa ett nytt kundkonto och ändra kundgruppen till Grossist.
1. Skapa en ny katalogregel i **Marknadsföring** > **Erbjudanden** > **Katalogprisregler** med följande parametrar:
   * Kundgrupper: Grossistaktiviteter:
   * Använd: *Använd som procentandel av originalet*
   * Rabatt: *50*


1. Skapa en ny produkt med price=100.
1. Logga in på klientsidan med det tidigare skapade kundkontot (om du redan var inloggad loggar du ut och loggar in igen).
1. Lägg produkten i kundvagnen. Produktpriset är 50 (normalpris 100) och Ordersumma: 55 (50 + 5 av leveranskostnaden).
1. Kör GraphQL API-anropet som beskrivs i [customerCart query](https://devdocs.magento.com/guides/v2.3/graphql/queries/customer-cart.html) i vår dokumentation för utvecklare.

<u>Förväntat resultat:</u>

Både API och klientdel har samma ordersumma med rabatten som katalogregeln ger.

<u>Faktiskt resultat:</u>

Ordersumman tillämpar inte katalogregelrabatt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Tillämpa korrigeringar med verktyget Korrigera kvalitet](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html).

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT finns i avsnittet Patchar i QPT.
