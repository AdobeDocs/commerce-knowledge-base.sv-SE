---
title: 'MDVA-41139: Konfigurerbara produkter blir obefintliga efter produktimport'
description: Korrigeringen MDVA-41139 åtgärdar ett problem där den konfigurerbara produkten inte finns i lager efter produktimporten när den enkla produktens kvantitet = 0 för en av dess källor. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 är installerat. Korrigerings-ID är MDVA-41139. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: e90ab578-50b9-4bc4-baf9-de4182e700ae
feature: Data Import/Export, Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-41139: Den konfigurerbara produkten blir inte i lager efter produktimporten

Korrigeringen MDVA-41139 åtgärdar ett problem där den konfigurerbara produkten inte finns i lager efter produktimporten när den enkla produktens kvantitet = 0 för en av dess källor. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 har installerats. Korrigerings-ID är MDVA-41139. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den konfigurerbara produkten blir inte i lager efter produktimporten när den enkla produktens kvantitet = 0 för en av dess källor.

<u>Förutsättningar</u>:

Lagermoduler är installerade.

<u>Steg som ska återskapas</u>:

1. Skapa en ny källa och aktie.
1. Skapa en konfigurerbar produkt med underordnade produkter som tilldelats standardkällan och den nya källan.
1. Ange värdet för standardlager för varje underordnad produkt = 0, och för annan stock > 0.
1. Den konfigurerbara produkten finns i lager.
1. Exportera den här produkten och importera den igen.

<u>Förväntade resultat</u>:

Den konfigurerbara produkten finns i lager eftersom den andra källan har en kvantitet på > 0.

<u>Faktiska resultat</u>:

Den konfigurerbara produkten är inte i lager.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
