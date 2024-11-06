---
title: 'MDVA-39605: TTL för Redis-cache (förfallodatum) har fel värde'
description: MDVA-39605-korrigeringen löser problemet där Redis cache TTL (förfallodatum) har fel värde. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-39605. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 7283838b-702d-4ddc-aa03-829dbf5aa91f
feature: Cache, Console, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# MDVA-39605: TTL för Redis-cache (förfallodatum) har fel värde

MDVA-39605-korrigeringen löser problemet där Redis cache TTL (förfallodatum) har fel värde. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-39605. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

TTL-värdet för Redis-cachen (förfallodatum) har ett felaktigt värde.

<u>Steg som ska återskapas</u>:

Testa korrigeringen genom att rensa cacheminnet och öppna en konfigurerbar produkt i butiken. Öppna sedan en terminal (konsol) och följ stegen nedan:

1. Kör kommandot: `redis-cli`.
1. Kör `KEYS "*PRICE"` (det ska bara finnas en nyckel i resultatet, till exempel `zc:ti:e54_PRICE`). Kopiera nyckeln.
1. Kör `SMEMBERS` följt av nyckeln från föregående steg (till exempel `SMEMBERS zc:ti:e54_PRICE`). Kopiera valfri tangent från resultatet (t.ex. e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Kör `KEYS "*<key>"` med nyckelnamnet från föregående steg för att hämta det fullständiga nyckelnamnet (till exempel `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`). Det ska bara finnas en nyckel i resultatet (till exempel `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Som du kanske märker är det fullständiga nyckelnamnet bara nyckelnamnet med prefixet `zc:k:`. Kopiera det fullständiga nyckelnamnet.
1. Kör `HGETALL` följt av det fullständiga nyckelnamnet från steg 4 för att kontrollera värdet. Värdet ska innehålla serialiserade data för associerade produkter för en relaterad konfigurerbar produkt.
1. Kör `TTL` följt av det fullständiga nyckelnamnet från steg 4 för att kontrollera om nyckeln har en förfallotid. Resultatet ska skilja sig från **-1** och **-2** och ska vara cirka 2592000 (30 dagar). Även om den förfallodag som anges i koden är ett år har Redis-biblioteket i Adobe Commerce en hög maxgräns på 2592000-tal.

<u>Förväntade resultat</u>:

Förfallogränsen är 2592000s

<u>Faktiska resultat</u>:

Förfallogränsen är **-1** eller **-2**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
