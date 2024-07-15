---
title: 'MDVA-38728: Om du ändrar synlighet för produkten skapas en URL-omskrivning för huvudwebbplatsen'
description: MDVA-38728-korrigeringen löser problemet där en ändring av produktsynligheten för den andra webbplatsen skapar en URL-omskrivning för huvudwebbplatsen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Patch-ID:t är MDVA-38728. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: ad1d5f82-294d-485d-acd3-28c3cd0fbf56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-38728: Om du ändrar synlighet för produkten skapas en URL-omskrivning för huvudwebbplatsen

MDVA-38728-korrigeringen löser problemet där en ändring av produktsynligheten för den andra webbplatsen skapar en URL-omskrivning för huvudwebbplatsen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Patch-ID:t är MDVA-38728. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du ändrar produktsynligheten för den andra webbplatsen skapas en URL-omskrivning för huvudwebbplatsen.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en webbplats, butik och butiksgranskning.
1. Skapa en enkel produkt.
1. Ange synligheten till **Inte synlig enskilt**.
1. Tilldela endast den andra webbplatsen produkten.
1. Fyll i alla andra obligatoriska fält.
1. Spara produkten.
1. Starta MySQL-köer:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. Gå till Produktlista.
1. Markera den skapade produkten och uppdatera synlighetsattributet med massuppdateringen till Katalog och Sök.
1. Kontrollera URL-omskrivningen.

<u>Förväntade resultat</u>:

Omskrivningen skapas för den andra webbplatsen där produkten är tilldelad.

<u>Faktiska resultat</u>:

Omskrivningen skapas för huvudwebbplatsen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
