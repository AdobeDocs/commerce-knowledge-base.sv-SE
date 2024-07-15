---
title: "ACSD-45257: Kundrabatt visas inte korrekt i GraphQL"
description: Korrigeringsfilen ACSD-45257 åtgärdar ett problem där kundvagnsrabatten inte visas korrekt i GraphQL. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 är installerat. Korrigerings-ID är ACSD-45257. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: 64576fa3-1160-4fc3-8458-4e622c30af74
feature: GraphQL, Marketing Tools, Orders, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-45257: Kundrabatt visas inte korrekt i GraphQL

Korrigeringsfilen ACSD-45257 åtgärdar ett problem där kundvagnsrabatten inte visas korrekt i GraphQL. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 är installerat. Korrigerings-ID är ACSD-45257. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.3-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundrabatten visas inte korrekt i GraphQL.

<u>Steg som ska återskapas</u>:

1. Gå till **Admin** > **Marknadsföring** > **Kampanjer** > **Kundprisregel**.
1. Lägg till en ny regel och tillämpa den på leveransbeloppet.
1. Lägg en produkt i kundvagnen med GraphQL.
1. Kontrollera kundvagnsinformation med en GraphQL-fråga.

<u>Förväntade resultat</u>:

Den totala rabatten inkluderar rabatten på fraktbeloppet i GraphQL svar.

<u>Faktiska resultat</u>:

Den totala rabatten återspeglar inte den rabatt som tillämpas på fraktbeloppet i GraphQL svar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
