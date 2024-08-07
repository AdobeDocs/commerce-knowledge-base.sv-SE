---
title: "MDVA-30845: utcheckningen av anslutningen till leveransleverantören misslyckas"
description: MDVA-30845-korrigeringen åtgärdar ett problem där *Tyvärr visas inga citattecken för den här beställningen just nu*-fel när det inte går att ansluta till UPS XML/USPS/DHL under utcheckningen och ingen annan leveransmetod är tillgänglig. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.2.
exl-id: 7be54213-1762-431b-bd3b-080c3d45f492
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-30845: Det går inte att checka ut en anslutning till en leveransleverantör

MDVA-30845-korrigeringen åtgärdar ett problem där *Tyvärr finns inga citattecken tillgängliga för den här beställningen just nu* -felet visas när det inte går att ansluta till UPS XML/USPS/DHL under utcheckningen och ingen annan leveransmetod är tillgänglig. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.3.5-p2.

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce lokalt och Adobe Commerce i molninfrastruktur 2.3.5-2.3.6.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Vid utcheckning visas *Tyvärr inga offerter för den här beställningen just nu*-fel när det inte går att ansluta till UPS XML/USPS/DHL, och ingen annan leveransmetod är tillgänglig.

<u>Steg att återskapa:</u>

1. Skapa en produkt.
1. Aktivera och konfigurera leveransmetoden för UPS XML.
1. Lägg produkten i varukorgen på butikssidan.
1. Se till att det finns fraktmetoder för UPS och frakt till fast pris.
1. Redigera värdfilen för att förhindra att USP ansluter till gatewayen.
1. I butiken försöker du få priser och fortsätta till kassan igen.

<u>Faktiskt resultat:</u>

*Det finns tyvärr inga offerter tillgängliga för den här beställningen just nu.*-fel visas och frakt med schablonbelopp är inte tillgängligt.

<u>Förväntat resultat:</u>

Inget felmeddelande visas och frakten till fast pris är tillgänglig.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.


## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
