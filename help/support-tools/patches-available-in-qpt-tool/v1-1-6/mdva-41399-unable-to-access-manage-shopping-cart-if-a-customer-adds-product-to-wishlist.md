---
title: 'MDVA-41399: Det går inte att komma åt kundvagnen om en kund lägger till en produkt i önskelistan'
description: MDVA-41399-korrigeringen löser problemet där administratörsanvändare inte kan komma åt sidan Hantera kundvagn om en kund lägger till en produkt i önskelistan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 är installerat. Korrigerings-ID är MDVA-41399. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 227653c6-2d20-4475-b973-b9fa58db815b
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-41399: Det går inte att komma åt Hantera kundvagn om en kund lägger till en produkt i önskelistan

MDVA-41399-korrigeringen löser problemet där administratörsanvändare inte kan komma åt sidan Hantera kundvagn om en kund lägger till en produkt i önskelistan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 har installerats. Korrigerings-ID är MDVA-41399. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändare kan inte komma åt sidan Hantera kundvagn om en kund lägger till en produkt i önskelistan.

<u>Förutsättningar</u>:

1. Skapa två eller flera produkter.
1. Skapa en kund.
1. Aktivera utvecklarläget.

<u>Steg som ska återskapas</u>:

1. Gå till Storefront och logga in som kund från villkoren.
1. Lägg till en produkt i önskelistan.
1. Gå till Admin-panelen och navigera till den skapade kundredigeringssidan och klicka på knappen **Hantera kundvagn** .

<u>Förväntade resultat</u>:

Administratörsanvändaren kan hantera kundvagnen.

<u>Faktiska resultat</u>:

Administratörsanvändaren får ett felmeddelande: *Ett fel har inträffat. Mer information finns i felloggen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
