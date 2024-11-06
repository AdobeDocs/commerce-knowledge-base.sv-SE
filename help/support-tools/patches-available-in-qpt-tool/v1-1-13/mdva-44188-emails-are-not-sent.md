---
title: '''MDVA-44188: E-postmeddelanden skickas inte till ID:n som innehåller ".-"'
description: MDVA-44188-korrigeringen åtgärdar ett problem där e-post inte skickas till e-post-ID:n som innehåller `.-`. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Patch-ID:t är MDVA-44188. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 2abd300a-6cf3-4973-9b36-1bba7b578378
feature: Communications
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-44188: E-postmeddelanden skickas inte till ID:n som innehåller &quot;.-&quot;

MDVA-44188-korrigeringen åtgärdar ett problem där e-post inte skickas till e-post-ID:n som innehåller `.-`. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Patch-ID:t är MDVA-44188. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att skicka e-post till e-post-ID:n som innehåller `.-` i användarnamnet.

<u>Steg som ska återskapas</u>:

1. Registrera en kund med en e-postadress som innehåller `.-`. Exempel: `.-foo@example.com`.
1. Beställ.

<u>Förväntade resultat</u>:

Användare med e-post-ID:t som innehåller `.-` får e-post som vanligt.

<u>Faktiska resultat</u>:

E-post skickas inte till e-post-ID:t som innehåller `.-`. Följande fel visas i felloggarna: *Det gick inte att lägga till en ogiltig e-postadress i postkön*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
