---
title: "MDVA-34943: Snabbbeställning kan inte lägga till 2+ produkter i kundvagnen"
description: MDVA-34943-korrigeringen löser problemet där en snabbbeställning inte kan lägga till två eller flera produkter i kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.2.
exl-id: fcff6a78-fe00-4352-b0bc-149bd411d999
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# MDVA-34943: Snabbbeställning kan inte lägga till 2+ produkter i kundvagnen

MDVA-34943-korrigeringen löser problemet där en snabbbeställning inte kan lägga till två eller flera produkter i kundvagnen. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.4.0-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användarna kan inte lägga till två eller flera produkter i kundvagnen i en snabbbeställning.

<u>Förutsättningar</u>:

Adobe Commerce med enkla produkter.

<u>Steg som ska återskapas</u>:

1. Gå till **Snabbordning** på Storefront (medan du inte är inloggad).
1. Ange en giltig SKU, klicka på produkten som visas i fältet Komplettera automatiskt och ange **Kvantitet** = *1*.
1. Ange samma giltiga SKU, men ändra skiftläge (ändra versaler till gemener eller ändra gemener till versaler) för det första tecknet, och klicka på den produkt som visas i fältet Komplettera automatiskt och ange **Kvantitet** = *1*.
1. Ange en `random_sting_value` for **SKU** och ange **Kvantitet** = *1*.
1. Ange **SKU** = *123123123* och ange **Kvantitet** = *1*.
1. Ta bort allt utom den första posten som du lade till i **Snabbordning** sida.
1. Ange den första SKU:n (liknar steg 2 ovan) i dialogrutan **Ange flera SKU:er** och klicka **Lägg till i listan**.
1. Detta ger en kvantitet på 2 för den första SKU:n och en rad för en `random_sting_value`.
1. Uppdatera sidan om du vill testa mer.
1. Detta resulterar i att det inte finns några SKU:er att beställa som förväntat.
1. Ange en `random_sting_value2` till **Ange flera SKU:er** och klicka **Lägg till i listan**.
1. Detta resulterar i två giltiga SKU:er från föregående och en `random_sting_value2`.

<u>Förväntade resultat</u>:

Två eller flera produkter kan läggas till i varukorgen som förväntat.

<u>Faktiska resultat</u>:

När den tas till **Kundvagn** den första tillagda produkten visas normalt, men för den andra produkten och alla efterföljande produkter som tillkommit i kundvagnen visas en *1 produkt kräver åtgärd*&quot; visas felmeddelande. Den andra eller eventuella ytterligare produkter listas på **Produkten måste åtgärdas** i **Kundvagn** sida.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
