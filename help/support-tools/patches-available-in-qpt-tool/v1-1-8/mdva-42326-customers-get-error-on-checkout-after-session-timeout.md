---
title: 'MDVA-42326: Kunder får felmeddelanden vid utcheckning efter timeout för session'
description: MDVA-42326-korrigeringen löser problemet där kunderna får ett felmeddelande vid utcheckning efter timeout-datumet för sessionen, även om beständig kundvagn är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 är installerat. Korrigerings-ID är MDVA-42326. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: Kunder får felmeddelanden vid utcheckning efter timeout för session

MDVA-42326-korrigeringen löser problemet där kunderna får ett felmeddelande vid utcheckning efter timeout-datumet för sessionen, även om beständig kundvagn är aktiverad. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 är installerat. Korrigerings-ID är MDVA-42326. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunderna får ett felmeddelande vid utcheckning efter sessionstimeout, även om beständig kundvagn är aktiverad.

<u>Förutsättningar</u>:

1. Gå till **Konfig** > **Allmänt** > **Webb** > **Inställningar för standardcookie** > **Cookie-livstid** och ange till **120**.
1. Gå till **Konfig** > **Kunder** > **Kundkonfiguration** > **Alternativ för onlinekunder** och ange båda värdena till **2**.
1. Gå till **Konfig** > **Kunder** > **Beständig kundvagn** och ange till **Aktivera**.
1. Gå till **Konfig** > **Försäljning** > **Betalningsmetoder** och inaktivera alla betalningsmetoder utom **Check-/penningbeställning** (den ska vara aktiverad).

<u>Steg som ska återskapas</u>:

1. Logga in som kund och lägg till några produkter i kundvagnen.
1. Kolla kundvagnen.
1. Vänta i två minuter (förvillkor anges). Sessionen bör timeout.
1. Klicka **Gå till kassan** och uppdatera inte sidan.
1. Checka ut som gäst, fyll i leveransadress och välj leveranssätt.
1. Klicka **Nästa**.
1. På **Granska och betala** sida, klicka **Montera beställning**. Eftersom endast en betalningsmetod är tillåten bör kunden kunna lägga ordern utan att välja betalningsmetod.

<u>Förväntade resultat</u>:

Kunden bör kunna lägga ordern.

<u>Faktiska resultat</u>:

Kunden får följande fel: *Adressvalideringen misslyckades: E-postmeddelandet har fel format*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
