---
title: 'MDVA-42509: Det gick inte att överföra CSV för snabbbeställning vilket resulterade i felet"Det går inte att skicka cookien"'
description: MDVA-42509-korrigeringen löser problemet där en CSV-fil inte kunde överföras för snabbbeställning vilket resulterade i *Det gick inte att skicka cookie-filen*. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 är installerat. Korrigerings-ID är MDVA-42509. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 7aa0e710-9a28-4531-b9cb-c82f654487f4
feature: B2B, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-42509: Det gick inte att överföra CSV för snabbbeställning vilket resulterade i felet&quot;Det går inte att skicka cookien&quot;

MDVA-42509-korrigeringen löser problemet där en CSV inte kunde överföras för snabbbeställning vilket resulterade i *Det gick inte att skicka cookie*-felet. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 är installerat. Korrigerings-ID är MDVA-42509. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du skapar en snabborder med ett stort antal produkter med hjälp av en CSV-fil visas ett cookie-fel: *Det går inte att skicka cookien*

<u>Steg som ska återskapas</u>:

1. Aktivera snabbordning genom att gå till **Lager** > **Inställningar** > **Konfigurationer** > **Allmänt** > **B2B-funktioner**.
1. Skapa ett kundkonto och gå till **Snabbbeställning** på den översta länken.
1. Försök att skapa en snabb beställning med en CSV-fil som har fler än 100 SKU:er.

<u>Förväntade resultat</u>:

Du kan skapa en snabb beställning med ett stort antal SKU:er.

<u>Faktiska resultat</u>:

Ett felmeddelande visas som relaterar till cookie-storleken.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
