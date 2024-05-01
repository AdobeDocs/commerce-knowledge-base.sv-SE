---
title: "ACSD-50858: Förbättrade prestanda för inläsning av banners-innehåll"
description: Använd patchen ACSD-50858 för att åtgärda Adobe Commerce-problemet där banderollens prestanda påverkas på kundvagn-/utcheckningssidan på grund av för stora DB-frågor och längre sidladdningstid.
exl-id: f9526d66-fc0e-44a0-8c72-b9f183004840
feature: Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-50858: Förbättrade prestanda för inläsning av banners-innehåll

Korrigeringsfilen ACSD-50858 åtgärdar ett problem med bannerprestanda på kundvagns-/utcheckningssidan: *överflödiga DB-frågor och längre sidinläsningstid*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31 är installerat. Korrigerings-ID är ACSD-50858. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Banderollens prestanda påverkas på korgs-/utcheckningssidan på grund av *överflödiga DB-frågor och längre sidinläsningstid*.

Detta korrigerades genom omfaktorisering av hur banners innehåll läses in, vilket minskade antalet DB-frågor med 99,99 % och sidinläsningstiden med cirka 99 %.

<u>Steg som ska återskapas</u>:

1. Logga in på Admin och skapa en enkel produkt.
1. Skapa en kund, antingen från Admin eller från frontend, och lägg till en leveransadress för den.
1. Flytta banners.php till `magento_root/pub/` mapp.
1. Generera banners med  `php pub/banners.php` -kommando. Det kommer att generera 10 000 enkla banners och 1 000 banners med försäljningsregler.
1. Logga in på kunden som skapats tidigare i klientorganisationen.
1. Lägg den produkt som skapats tidigare i kundvagnen.
1. Gå till kassan (kassan/kundvagnen).
1. Övervaka `banner/ajax/load` inläsningstid:

   * Utan `bin/magento dev:query-log:enable`
   * Med `bin/magento dev:query-log:enable`

     ```
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u>Förväntade resultat</u>:

Minska antalet DB-frågor för `magento_banner_content` och inläsningstid för kundvagn/utcheckning.

<u>Faktiska resultat</u>:

Öka antalet DB-frågor för `magento_banner_content` och inläsningstid för kundvagn/utcheckning.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Ytterligare information

<u>banners.php content</u>:

```php
\Banner::class);
    $banner->setIsEnabled(
        \Magento\Banner\Model\Banner::STATUS_ENABLED
    )->setName(
        'Test Dynamic Block '.$i
    )->setTypes(
        ''
    )->setStoreContents(
        [0 => 'Dynamic Block Content '.$i]
    )->save();
}

$objectManager = \Magento\Framework\App\ObjectManager::getInstance();

/** @var \Magento\SalesRule\Model\Rule $salesRule */
$salesRule = $objectManager->create(\Magento\SalesRule\Model\Rule::class);
$salesRule->setData(
    [
        'name' => '50% Off ',
        'is_active' => 1,
        'customer_group_ids' => [\Magento\Customer\Model\GroupManagement::NOT_LOGGED_IN_ID],
        'coupon_type' => \Magento\SalesRule\Model\Rule::COUPON_TYPE_NO_COUPON,
        'conditions' => [
            [
                'type' => \Magento\SalesRule\Model\Rule\Condition\Address::class,
                'attribute' => 'base_subtotal',
                'operator' => '>',
                'value' => 0
            ]
        ],
        'simple_action' => 'by_percent',
        'discount_amount' => 50,
        'discount_step' => 0,
        'stop_rules_processing' => 1,
        'website_ids' => [
           1
        ]
    ]
);
$salesRule->save();

for ($i = 0; $i < 1000; $i++) {

    $banner = $objectManager->create(\Magento\Banner\Model\Banner::class);
    $banner->setData(
        [
            'name' => 'Get 50% Off ',
            'is_enabled' => \Magento\Banner\Model\Banner::STATUS_ENABLED,
            'types' => [], /*Any Banner Type*/
            'store_contents' => ['<img src="http://example.com/banner_40_percent_off.png" />'],
            'banner_sales_rules' => [$salesRule->getId()],
        ]
    );
    $banner->save();
}
```

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
