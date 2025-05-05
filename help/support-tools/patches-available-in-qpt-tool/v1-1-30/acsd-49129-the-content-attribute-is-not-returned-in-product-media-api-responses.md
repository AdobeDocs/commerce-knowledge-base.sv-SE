---
title: 'ACSD-49129: Attributet "Content" returneras inte i API-svar för produktmedia'
description: Använd korrigeringsfilen ACSD-49129 för att åtgärda Adobe Commerce-problemet där attributet *content* (*base64-bildkod*) inte returneras i programmeringsgränssnittssvaren för "rest/V1/products/sku/media".
exl-id: b7022046-3f52-4880-81b8-977ed270773f
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-49129: Attributet &quot;Content&quot; returneras inte i API-svar för produktmedia

Korrigeringen ACSD-49129 åtgärdar ett problem där attributet *content* (*[!UICONTROL base64 image code]*) inte returneras i `rest/V1/products/sku/media` API-svaren för produktmedia. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.30 har installerats. Korrigerings-ID är ACSD-49129. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Attributet *content* (*[!UICONTROL base64 image code]*) returneras inte i `rest/V1/products/sku/media` API-svar för produktmedia.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt med en bild.
1. Skicka *GET REST API*-begäran till `rest/V1/products/<sku>/media` och `rest/V1/products/<sku>/media/<entryId>`.
1. Kontrollera API-svaren.

<u>Förväntade resultat</u>

Attributet *content* med data är tillgängligt via REST API.

<u>Faktiska resultat</u>

Attributet *content* finns inte i API-svaren.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
