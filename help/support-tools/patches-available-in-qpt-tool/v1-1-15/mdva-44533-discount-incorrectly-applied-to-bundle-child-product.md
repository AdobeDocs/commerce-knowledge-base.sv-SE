---
title: 'MDVA-44533: Rabatten tillämpas felaktigt på paketerade underordnade produkter'
description: MDVA-44533-korrigeringen åtgärdar ett problem där en rabatt felaktigt tillämpas på en paketerad underordnad produkt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Patch-ID:t är MDVA-44533. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 84302ed4-d850-45e4-8b5b-44495f9df820
feature: Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-44533: Rabatten tillämpas felaktigt på paketerade underordnade produkter

MDVA-44533-korrigeringen åtgärdar ett problem där en rabatt felaktigt tillämpas på en paketerad underordnad produkt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Patch-ID:t är MDVA-44533. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Rabatten tillämpas felaktigt på en paketerad underordnad produkt.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt till priset 50$.
1. Skapa en paketerad produkt och tilldela den enkla produkten som det enda alternativet för den paketerade produkten.
1. Skapa en kundprisregel med:

   * Villkor: Om det totala beloppet är större än 130$
   * Åtgärd: Rabatt på 10$ tillämpas med fast belopp

1. Gå till butiken och lägg till paketprodukten i vagnen med kvantitet = 1.
1. Gå till kundvagnen och kontrollera att totalkostnaden för paketprodukten är 50$ och att rabatten inte gäller.
1. Ändra kvantiteten till 2 och uppdatera vagnen. Den totala kostnaden för den paketerade produkten bör nu vara 100$.

<u>Förväntade resultat</u>:

Rabatten tillämpas inte eftersom delsumman är 100\$, vilket är mindre än 130\$ i regelvillkoret.

<u>Faktiska resultat</u>:

Rabatten tillämpas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
