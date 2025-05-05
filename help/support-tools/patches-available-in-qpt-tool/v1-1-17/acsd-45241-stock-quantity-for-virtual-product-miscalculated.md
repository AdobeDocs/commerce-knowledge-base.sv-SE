---
title: "ACSD-45241: Felaktig beräkning av den virtuella produktens lagerkvantitet"
description: Korrigeringen ACSD-45241 åtgärdar ett problem där den virtuella produktens lagerkvantitet inte beräknas korrekt efter att en kreditnota har skapats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 är installerat. Korrigerings-ID är ACSD-45241. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.
exl-id: 4be97da9-d399-419a-816e-cf65f15cc3be
feature: Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-45241: Felaktig beräkning av den virtuella produktens lagerkvantitet

Korrigeringen ACSD-45241 åtgärdar ett problem där den virtuella produktens lagerkvantitet inte beräknas korrekt efter att en kreditnota har skapats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 är installerat. Korrigerings-ID är ACSD-45241. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerkvantiteten för en virtuell produkt beräknas inte korrekt efter att en kreditnota har skapats.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med en virtuell produkt som underordnad produkt i Commerce Admin.
1. Kontrollera att båda produkterna som skapats i steg 1 finns i lager.
1. Markera kvantiteten för den virtuella produkten som skapats i steg 1 som 100 och behåll även den säljbara kvantiteten 100.
1. Lägg produkten i kundvagnen.
1. Gör en beställning med den virtuella produkten som skapats i steg ett.
1. Behåll orderstatus som Väntande. Du behöver inte behandla betalningen.
1. `order_created` post skapades i `inventory_reservation`. Den virtuella produktkvantiteten visar 100 med säljbar kvantitet som 99.
1. Öppna ordern och gå till **Faktura** > **Skicka faktura**.
1. `invoice_created` post skapades i `inventory_reservation`. Den virtuella produktkvantiteten är nu 99 och den säljbara kvantiteten är 99.
1. Skapa en kreditnota utan att välja **Återgå till Stock**.

<u>Förväntade resultat</u>:

Ingen ny post skapas i `inventory_reservation` och lagerkvantiteten för den virtuella produkten är oförändrad.

<u>Faktiska resultat</u>:

En `creditmemo_created`-post skapas i `inventory_reservation` och den virtuella produktlagerkvantiteten justeras till 98 med försäljningsbar kvantitet som 99.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
