---
title: "MDVA-42237: Specialpriset för den konfigurerbara produkten har inte uppdaterats"
description: MDVA-42237-korrigeringen åtgärdar ett problem där den konfigurerbara produktens specialpris inte uppdateras efter ändringar av dess underproduktspris. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 är installerat. Korrigerings-ID är MDVA-42237. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 3e890448-8368-4eb2-ab64-c04cdacf20bb
feature: Admin Workspace, Configuration, Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42237: Specialpriset för den konfigurerbara produkten har inte uppdaterats

MDVA-42237-korrigeringen åtgärdar ett problem där den konfigurerbara produktens specialpris inte uppdateras efter ändringar av dess underproduktspris. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 är installerat. Korrigerings-ID är MDVA-42237. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Specialpriset för den konfigurerbara produkten uppdateras inte efter ändringar av dess underproduktspris.

<u>Steg som ska återskapas</u>:

1. Gå till **Admin** > **System** > **Indexhantering** och ställ in **Indexläge** på **Uppdatera enligt schema** för alla index.
1. Skapa en konfigurerbar produkt med en enkel produkt och ange ett specialpris för delprodukten.
1. Kontrollera att specialpriset visas på Storefront.
1. Ta bort specialpriset med GraphQL och kontrollera produktpriset i Store igen.

<u>Förväntade resultat</u>:

Specialpriset visas inte längre på Storefront.

<u>Faktiska resultat</u>:

Priset är inte uppdaterat på Storefront.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
