---
title: 'MDVA-31399 patch: Subtotal (Incl. Skatt) i kundvagnsregelvillkor'
description: MDVA-31399-korrigeringen lägger till *Delsumma (Incl. Skatt)* alternativ till [villkor för kundprisregel](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), som åtgärdar problemet där det var omöjligt att tillämpa en kundprisregel baserad på delsumma (Incl. Moms). Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 är installerat.
exl-id: ea0f4060-753a-4b0d-896b-fff54ffd1a82
feature: Marketing Tools, Orders, Shopping Cart, Taxes
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-31399-korrigering: Delsumma (inkl. Skatt) i kundvagnsregelvillkor

MDVA-31399-korrigeringen lägger till *delsumman (Incl. Skatt)*-alternativ till [villkor för kundprisregel](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), som åtgärdar problemet där det inte var möjligt att tillämpa en kundprisregel baserad på delsumma (Inkl. Moms). Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 är installerat.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.2 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det är omöjligt att tillämpa en kundvagnsprisregel som baseras på delsumma (Inkl. Moms).

<u>Steg som ska återskapas</u>:

1. Konfigurera produktpriset för att inkludera moms.
1. Skapa en momsregel och en skattesats på 20 %.
1. Skapa en produkt med **Price** = *100* (detta pris inkluderar moms).
1. Skapa en ny kundvagnsprisregel med kupongen &quot;10off&quot; för att tillämpa den fasta rabattnivån $10 om delsumman uppfyller följande villkor:

**Villkor**: *Om ALLA dessa villkor är TRUE:*        * **Delsumma** är lika med eller större än 100.*

<u>Förväntade resultat</u>:

Det går att skapa en kundvagnsregel med kupong för att tillämpa rabatt på delsumman inklusive moms.

<u>Faktiska resultat</u>:

Det finns två alternativ i kundvagnsregelvillkoren: *Delsumma* och *Delsumma (exkl. Moms)*, och den som har valts, gäller regeln endast delsumma exklusive moms.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [korrigeringsfilerna i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
