---
title: 'MDVA-39605: TTL för Redis-cache (förfallodatum) har fel värde'
description: MDVA-39605-korrigeringen löser problemet där Redis cache TTL (förfallodatum) har fel värde. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-39605. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 7283838b-702d-4ddc-aa03-829dbf5aa91f
feature: Cache, Console, Services
role: Admin
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# MDVA-39605: TTL för Redis-cache (förfallodatum) har fel värde

MDVA-39605-korrigeringen löser problemet där Redis cache TTL (förfallodatum) har fel värde. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-39605. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

TTL-värdet för Redis-cachen (förfallodatum) har ett felaktigt värde.

<u>Steg som ska återskapas</u>:

Testa korrigeringen genom att rensa cacheminnet och öppna en konfigurerbar produkt i butiken. Öppna sedan en terminal (konsol) och följ stegen nedan:

1. Kör kommandot: `redis-cli`.
1. Kör `KEYS "*PRICE"` (det ska bara finnas en tangent i resultatet, till exempel `zc:ti:e54_PRICE`). Kopiera nyckeln.
1. Kör `SMEMBERS` följt av tangenten från föregående steg (till exempel `SMEMBERS zc:ti:e54_PRICE`). Kopiera valfri tangent från resultatet (t.ex. e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Kör `KEYS "*<key>"` med nyckelnamnet från föregående steg för att få hela nyckelnamnet (till exempel `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`). Det ska bara finnas en tangent i resultatet (till exempel `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Som du kanske märker är det fullständiga nyckelnamnet bara nyckelnamnet med prefixet &quot;`zc:k:`&quot;. Kopiera det fullständiga nyckelnamnet.
1. Kör `HGETALL` följt av det fullständiga nyckelnamnet från steg 4 för att kontrollera värdet. Värdet ska innehålla serialiserade data för associerade produkter för en relaterad konfigurerbar produkt.
1. Kör `TTL` följt av det fullständiga nyckelnamnet från steg 4 för att kontrollera om nyckeln har en förfallotid. Resultatet ska skilja sig från **-1** och **-2** och bör vara cirka 2592000 (30 dagar). Även om den förfallodag som anges i koden är ett år har Redis-biblioteket i Adobe Commerce en hög maxgräns på 2592000-tal.

<u>Förväntade resultat</u>:

Förfallogränsen är 2592000s

<u>Faktiska resultat</u>:

Förfallogränsen är inställd på **-1** eller **-2**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
