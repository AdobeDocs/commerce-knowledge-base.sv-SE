---
title: 'MDVA-31282: dubbel auktorisering för Paypal PayFlow Pro'
description: MDVA-31282-korrigeringen löser problemet när dubbla auktoriseringar inträffar på Paypal PayFlow Pro i Adobe Commerce. De dubbla auktoriseringarna innebär också att PayFlow Pros filter för bedrägeri kringgås och att transaktionsavgifterna dubbleras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat.
exl-id: f239012e-e1bd-474b-aad2-7218ec3a3d1b
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31282: dubbel auktorisering för Paypal PayFlow Pro

MDVA-31282-korrigeringen löser problemet när dubbla auktoriseringar inträffar på Paypal PayFlow Pro i Adobe Commerce. De dubbla auktoriseringarna innebär också att PayFlow Pros filter för bedrägeri kringgås och att transaktionsavgifterna dubbleras. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.2 - 2.3.3 och 2.3.5 - 2.3.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Dubbla auktoriseringar görs i PayPal PayFlow Pro i Adobe Commerce och leder till att man kringgår bedrägerifiltren i PayFlow Pro och dubblerar transaktionsavgifterna.

<u>Förutsättningar</u>:

Konfigurera betalningsmetoden PayPal PayFlow Pro.

<u>Steg som ska återskapas</u>:

1. Gå till fronten som gästkund.
1. Lägg till produkter i **Kundvagn** från produktsidor.
1. Gå till **Utcheckning**.
1. Ange **Leveransadress** som en adress i Land \#1 (Exempel: brittisk adress) och välj en leveransmetod.
1. Välj **PayPal PayFlow Pro** som betalningsmetod. Ange **faktureringsadressen** som en adress i Land \#2 (Exempel: USA-adress).
1. Ange kreditkortsdata och beställ.
1. Navigera till **Försäljning** > **Beställningar** i administratören och observera skapad ordning.

<u>Förväntade resultat</u>:

* Betalningsinformationsblocket visar: *&quot;Utlösta bedrägerifilter: RESPMSG: Undergranskas av bedrägeritjänsten*. *Beställningen har statusen Misstänkt bedrägeri*.
* Paypal PayFlow Pro visar en enda auktoriseringstransaktion som förväntat.

<u>Faktiska resultat</u>:

* Betalningsinformationsblocket visar: *&quot;Utlösta bedrägerifilter: RESPMSG: Undergranskas av bedrägeritjänsten*. *Beställningen bearbetar status:*.
* Paypal PayFlow Pro visar transaktioner med dubbel auktorisering.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
