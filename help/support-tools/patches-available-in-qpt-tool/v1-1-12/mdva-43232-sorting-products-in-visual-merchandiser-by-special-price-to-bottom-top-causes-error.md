---
title: "MDVA-43232: Sortering av produkter i visuell handlare efter specialpris till överkant (eller underkant) orsakar ett fel"
description: Korrigeringen MDVA-43232 åtgärdar ett problem där sortering av produkter i visuell handlare efter specialpris till överkant (eller underkant) orsakar ett fel när kategorin sparas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-43232. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: e958a219-5e93-4ae4-94cb-f478f82ad060
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-43232: Sortering av produkter i visuell handlare efter specialpris till överkant (eller underkant) orsakar ett fel

Korrigeringen MDVA-43232 åtgärdar ett problem där sortering av produkter i visuell handlare efter specialpris till överkant (eller underkant) orsakar ett fel när kategorin sparas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-43232. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du sorterar produkter i visuell återförsäljare efter specialpris överst (eller nederst) uppstår ett fel när du sparar kategorin.

<u>Steg som ska återskapas</u>:

1. Kontrollera att det finns två webbplatser.
1. Navigera till **Lager** > **Konfiguration** > **Katalog** > **Pris** och ange Katalogens prisomfång = webbplats.
1. Navigera återigen till **Lager** > **Konfiguration** > **Katalog** > **Visual Merchandiser** > **Synliga attribut för kategoriregler** > och lägg till specialpris.
1. Skapa en enkel produkt och tilldela produkterna till båda webbplatserna.
1. Lägg till ett specialpris i standardomfånget för produkten.
1. Byt till den andra butikens omfattning och åsidosätt både priset och specialpriset för den produkten.
1. Gör en `catalog_product_price`-omindexering.
1. Gå till **Katalog** > **Kategorier** och skapa en ny kategori.
1. Lägg till en kategoriregel för att filtrera produkter som har ett särskilt pris.
1. Spara kategorin.
1. Under avsnittet Produkter i kategorin anger du Sorteringsordning = Specialpris överst (eller nederst).
1. Spara kategorin igen.

<u>Förväntade resultat</u>:

Kategorin sparas utan fel.

<u>Faktiska resultat</u>:

Ett undantag genereras:

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
