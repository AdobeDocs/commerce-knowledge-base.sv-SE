---
title: "MDVA-35982: Kan inte skicka vissa beställningar"
description: MDVA-35982-korrigeringen åtgärdar felet när en administratörsanvändare som är begränsad till en viss webbplats inte kan skapa en leverans för den beställning som finns på samma webbplats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-35982. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: f41c6572-66bb-4697-93e3-da34b81829e2
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-35982: Kan inte skicka vissa beställningar

MDVA-35982-korrigeringen åtgärdar felet när en administratörsanvändare som är begränsad till en viss webbplats inte kan skapa en leverans för den beställning som finns på samma webbplats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-35982. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.5-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Merchant kan inte leverera vissa order.

<u>Steg som ska återskapas</u>:

1. Välj en produktwebbplats för produkten förutom standardbutiken. Mer information finns i [Produkt på webbplatser](https://docs.magento.com/user-guide/catalog/settings-basic-websites.html) i användarhandboken.
1. Skapa en användarroll för administratören med anpassade rollomfång, där standardwebbplatsen/standardbutiken inte är vald. Mer information finns i [Definiera en roll](https://docs.magento.com/user-guide/system/permissions-user-roles.html#define-a-role) i användarhandboken.
1. Öppna produkten i redigeringsläge och ange ett grupppris för den här produkten i **Avancerade priser**. Mer information finns i [Grupppris](https://docs.magento.com/user-guide/catalog/product-price-group.html) i användarhandboken.
1. Skapa en beställning med den här produkten.
1. Logga in under administratören med den här användarrollen och skapa en leverans. Mer information finns i [Skapa en leverans](https://docs.magento.com/user-guide/sales/shipments-create.html) i användarhandboken.

<u>Förväntade resultat</u>:

Leveransen skapas.

<u>Faktiska resultat</u>:

Följande fel visas:

`"0":"Notice: Undefined offset: XX in \/vendor\/magento\/module-catalog\/Model\/Product\/Attribute\/Backend\/GroupPrice\/AbstractGroupPrice.php on line 290"`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
