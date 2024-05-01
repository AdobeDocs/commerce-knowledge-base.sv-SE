---
title: 'ACSD-53204: *Det går inte att spara produkten* fel vid samtidig begäran om att lägga till bilder i galleriet'
description: Använd patchen ACSD-53204 för att åtgärda Adobe Commerce-problemet där *Felet inte kan sparas* uppstår när du gör samtidiga begäranden om att lägga till bilder i produktgalleriet med resten/V1/products/&lt;sku&gt;/media endpoint.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: dcea2621-66cf-49d1-bba6-b61c70716e84
source-git-commit: e1ab32a4540ea7483f7f2b8464ef3e4b0ecbbac7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53204: &quot;*Det går inte att spara produkten*&quot; fel vid samtidig begäran om att lägga till bilder i galleriet

Korrigeringen ACSD-53204 åtgärdar ett problem där &quot;*Det går inte att spara produkten*&quot; uppstår när samtidiga begäranden om att lägga till bilder i produktgalleriet görs med `rest/V1/products/<sku>/media` slutpunkt. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.39 är installerat. Korrigerings-ID är ACSD-53204. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

&quot;*Det går inte att spara produkten*&quot; uppstår när samtidiga begäranden om att lägga till bilder i produktgalleriet görs med `rest/V1/products/<sku>/media` slutpunkt.

<u>Steg som ska återskapas</u>:

1. Logga in på Admin Panel.
1. Skapa en produkt med SKU p1.
1. Gör flera samtidiga begäranden till `rest/V1/products/<sku>/media` slutpunkt för överföring av flera bilder samtidigt.

<u>Förväntade resultat</u>:

Bilderna sparas utan fel.

<u>Faktiska resultat</u>:

&quot;*Det går inte att spara produkten*&quot; returneras då och då.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
