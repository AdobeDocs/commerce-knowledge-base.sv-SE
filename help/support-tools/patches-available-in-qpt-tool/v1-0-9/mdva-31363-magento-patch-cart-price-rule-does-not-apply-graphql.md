---
title: 'MDVA-31363-korrigering: Bildens prisregel gäller inte (GraphQL)'
description: MDVA-31363-korrigeringen åtgärdar ett problem där kundvagnsregeln med kupong inte gäller via GraphQL när åtgärden Fast beloppsrabatt för hel kundvagn används. Den här korrigeringen är tillgänglig när QPT (Quality Patches Tool) 1.0.9 är installerat. Problemet är schemalagt att åtgärdas i Adobe Commerce version 2.4.2.
exl-id: f64fbbb1-b5fd-4624-bcdd-d1e6c1f9acfe
feature: GraphQL, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-31363-korrigering: Kortprisregeln gäller inte (GraphQL)

>[!WARNING]
>
>En ny patch som heter MDVA-33975 åtgärdar GraphQL problem med prisberäkning. MDVA-31363 skrivs av och du bör använda MDVA-33975-patchen. Information om hur du får åtkomst till den här korrigeringen finns i [MDVA-33975-korrigeringen: GraphQL prisberäkningar](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

MDVA-31363-korrigeringen åtgärdar ett problem där kundvagnsregeln med kupong inte gäller via GraphQL när åtgärden Fast beloppsrabatt för hel kundvagn används. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 är installerat. Problemet är schemalagt att åtgärdas i Adobe Commerce version 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.4.0

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.2 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om offertsummorna beräknas om innan ett svar ges om offertpriser går tillämpade regler förlorade.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Skapa en kundvagnsprisregel med en fast beloppsrabatt för hela vagnen.
1. Skapa en ny kundvagn med GraphQL.
1. Spara kortet\_id från svaret och lägg till produkten från steg 1 i kundvagnen med GraphQL.
1. Aktivera kundvagnsprisregeln genom att lägga kupongkoden i kundvagnen med GraphQL.
1. Kontrollera priset som svar.

<u>Förväntade resultat</u>:

Rabatten tillämpas.

<u>Faktiska resultat</u>:

Rabatten tillämpas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [korrigeringsfilerna i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
