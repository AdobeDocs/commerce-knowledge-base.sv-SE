---
title: 'MDVA-34023-korrigering: Felet "Ingen sådan entitet med addressId"'
description: MDVA-34023-korrigeringen löser problemet där "Inga sådana entiteter med adressId"-fel inträffar slumpmässigt i en kunds webbläsare.
exl-id: bdf8f97d-856a-4dd7-bf21-941d1493496c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-34023-korrigering: Felet &quot;Ingen sådan entitet med addressId&quot;

Korrigeringen MDVA-34023 löser problemet där `No such entity with addressId` fel inträffar slumpmässigt i en kunds webbläsare.

Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.15 är installerat. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.3.1

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce i molninfrastruktur och Adobe Commerce lokalt 2.3.0 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till **Butiker** > **Inställningar** > **Konfiguration** > **Fliken Kunder** > **Beständig kundvagn**.
1. Ange **Aktivera beständighet** = *Ja*, ange **Rensa beständighet vid utloggning** = *Nej*.    ![persistent_shopping_cart_magento_2.4.1.png](/help/support-tools/patches-available-in-qpt-tool/assets/persistent_shopping_cart_magento_2.4.1.png)
1. Skapa en ny kund och definiera standardadresserna för frakt och fakturering.
1. Logga ut.
1. Logga in med kryssrutan **Kom ihåg mig** markerad.
1. Gå till databastabellen `customer_entity` och ändra ID:n för `default_billing` och `default_shipping` till ID:n som inte finns.
1. Logga ut.

<u>Förväntade resultat</u>:

Inga fel visas som förväntat.

<u>Faktiska resultat</u>:

Undantagsloggen genereras:

```php
Exception.log:
{"0":"No such entity with addressId = XXXXX","1":"#0 /vendor\/magento\/module-customer\/Model\/AddressRegistry.php(49): Magento\\Framework
Exception
NoSuchEntityException::singleField('addressId', 'XXXXX')
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
