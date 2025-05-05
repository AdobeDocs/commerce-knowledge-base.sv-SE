---
title: 'MDVA-42326: Kunder får felmeddelanden vid utcheckning efter timeout för session'
description: MDVA-42326-korrigeringen löser problemet där kunderna får ett felmeddelande vid utcheckning efter timeout-datumet för sessionen, även om beständig kundvagn är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 är installerat. Korrigerings-ID är MDVA-42326. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: Kunder får felmeddelanden vid utcheckning efter timeout för session

MDVA-42326-korrigeringen löser problemet där kunderna får ett felmeddelande vid utcheckning efter timeout-datumet för sessionen, även om beständig kundvagn är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 har installerats. Korrigerings-ID är MDVA-42326. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunderna får ett felmeddelande vid utcheckning efter sessionstimeout, även om beständig kundvagn är aktiverad.

<u>Förutsättningar</u>:

1. Gå till **Konfiguration** > **Allmänt** > **Webb** > **Standardinställningar för cookie** > **Kakens livstid** och ange **120**.
1. Gå till **Konfiguration** > **Kunder** > **Kundkonfiguration** > **Alternativ för onlinekunder** och ange båda värdena till **2**.
1. Gå till **Konfiguration** > **Kunder** > **Beständig kundvagn** och ange **Aktivera**.
1. Gå till **Konfig** > **Försäljning** > **Betalningsmetoder** och inaktivera alla betalningsmetoder utom **Kontrollera/betala-order** (den ska vara aktiverad).

<u>Steg som ska återskapas</u>:

1. Logga in som kund och lägg till några produkter i kundvagnen.
1. Kolla kundvagnen.
1. Vänta i två minuter (förvillkor anges). Sessionen bör timeout.
1. Klicka på **Gå till kassan** och uppdatera inte sidan.
1. Checka ut som gäst, fyll i leveransadress och välj leveranssätt.
1. Klicka på **Nästa**.
1. Klicka på **Placera beställning** på sidan **Granska och betalningar**. Eftersom endast en betalningsmetod är tillåten bör kunden kunna lägga ordern utan att välja betalningsmetod.

<u>Förväntade resultat</u>:

Kunden bör kunna lägga ordern.

<u>Faktiska resultat</u>:

Kunden får följande fel: *Adressvalidering misslyckades: E-postmeddelandet har fel format*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
