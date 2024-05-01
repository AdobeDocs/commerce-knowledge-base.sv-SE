---
title: 'ACSD-46988: API-begäran för GraphQL-valuta returnerar null-värden'
description: Korrigeringen för ACSD-46988 åtgärdar ett problem där API-begäran för GraphQL-valuta returnerar null-värden för en anpassad valuta. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 är installerat. Korrigerings-ID är ACSD-46988. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: 8da0ab99-8db9-4222-9400-6df1520267f0
feature: REST, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-46988: API-begäran för GraphQL-valuta returnerar null-värden

Korrigeringen för ACSD-46988 åtgärdar ett problem där API-begäran för GraphQL-valuta returnerar null-värden för en anpassad valuta. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 är installerat. Korrigerings-ID är ACSD-46988. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

API-begäran för GraphQL-valuta returnerar null-värden för en anpassad valuta.

<u>Steg som ska återskapas</u>:

1. Konfigurera anpassad valuta i administratören. Gå till **System** > **Konfiguration** > **Allmänt** > **Valutainställningar**.
1. Skicka en GraphQL-begäran med följande nyttolast:

<pre>
<code class="language-graphql">
{
    currency {
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates {
            currency_to
            rate
        }
    }
}
</code>
</pre>

<u>Förväntade resultat</u>:

Begäran returnerar valutavärden i stället för null-värden.

<u>Faktiska resultat</u>:

Begäran returnerar flera null-värden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Verktyg för kvalitetspatchar > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden för verktyget Kvalitetspatchar.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Ytterligare steg krävs efter installationen av korrigeringsfilen

För lokala användare:

* Kör: `composer require symfony/intl:"~5.4.11"`

För molnanvändare:

* Kör: `composer require symfony/intl:"~5.4.11"`
* Push `composer.json` och `composer.lock` till Git-databasen tillsammans med patchfilen.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i guiden Verktyget för kvalitetskorrigeringar.
