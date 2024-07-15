---
title: 'MDVA-30945: ett allvarligt fel uppstod vid tillägg och uppdatering av kundvagnsåtgärder'
description: MDVA-30945-korrigeringen åtgärdar ett fel där du får ett allvarligt fel *Anrop till en medlemsfunktion getValue() på null i CartItemProcessor.php* för modulkonfigurerbara produkter när kundvagnar uppdateras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 0950e91b-900b-421d-91e7-abbfca4f30be
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-30945: ett allvarligt fel uppstod vid tillägg och uppdatering av kundvagnsåtgärder

MDVA-30945-korrigeringen åtgärdar ett fel där du får ett allvarligt fel *Anrop till en medlemsfunktion getValue() på null i CartItemProcessor.php* för modulen konfigurerbar-produkt vid uppdatering av kundvagnar. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett allvarligt PHP-fel när produkterna i kundvagnen har uppdaterats i Admin.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt utan alternativ i Commerce Admin.
1. Lägg den i kundvagnen på butiken.
1. Gå tillbaka till Admin, lägg till konfigurerbara alternativ för produkten och spara ändringarna.
1. Uppdatera kundvagnssidan på butiken.

<u>Förväntade resultat</u>:

Följande valideringsmeddelande visas på kundvagnssidan: *Vissa produkter nedan har inte alla alternativ som krävs*.

<u>Faktiska resultat</u>:

Kundvagnssidan är tom. I PHP `error.log` loggas följande fel: *Ohanterat undantag &#39;Error&#39; med meddelandet &#39;Call to a member function getValue() on null&#39; i vendor/magento/module-configurable-product/Model/Quote/Item/CartItemProcessor.php:76*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
