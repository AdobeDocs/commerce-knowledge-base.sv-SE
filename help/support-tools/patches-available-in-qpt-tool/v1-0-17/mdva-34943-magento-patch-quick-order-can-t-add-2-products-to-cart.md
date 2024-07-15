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

MDVA-34943-korrigeringen löser problemet där en snabbbeställning inte kan lägga till två eller flera produkter i kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce i molninfrastruktur 2.4.0-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användarna kan inte lägga till två eller flera produkter i kundvagnen i en snabbbeställning.

<u>Förutsättningar</u>:

Adobe Commerce med enkla produkter.

<u>Steg som ska återskapas</u>:

1. Gå till **Snabbordning** på Storefront (utan att vara inloggad).
1. Ange en giltig SKU, klicka på produkten som visas i fältet Komplettera automatiskt och ange **Kvantitet** = *1*.
1. Ange samma giltiga SKU, men ändra skiftläget (ändra versaler till gemener eller ändra gemener till versaler) för det första tecknet, och klicka på produkten som visas i fältet för automatisk komplettering och ange **Kvantitet** = *1*.
1. Ange `random_sting_value` för **SKU** och ange **Kvantitet** = *1*.
1. Ange **SKU** = *123123123* och ange **Kvantitet** = *1*.
1. Ta bort allt utom den första posten som du lade till på sidan **Snabbordning**.
1. Ange den första SKU:n (liknande steg 2 ovan) i fältet **Ange flera SKU:er** och klicka på **Lägg till i lista**.
1. Detta resulterar i kvantiteten 2 för den första SKU:n och en rad för `random_sting_value`.
1. Uppdatera sidan om du vill testa mer.
1. Detta resulterar i att det inte finns några SKU:er att beställa som förväntat.
1. Ange `random_sting_value2` i fältet **Ange flera SKU** och klicka på **Lägg till i lista**.
1. Detta resulterar i två giltiga SKU:er från föregående och en `random_sting_value2`.

<u>Förväntade resultat</u>:

Två eller flera produkter kan läggas till i varukorgen som förväntat.

<u>Faktiska resultat</u>:

När den läggs till på sidan **kundvagn** visas den första tillagda produkten normalt, men för den andra produkten och alla efterföljande produkter som läggs till i kundvagnen visas felmeddelandet *1-produkten kräver åtgärd*. Den andra eller eventuella ytterligare produkter visas i avsnittet **Produkten kräver uppmärksamhet** på sidan **Kundvagn**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
