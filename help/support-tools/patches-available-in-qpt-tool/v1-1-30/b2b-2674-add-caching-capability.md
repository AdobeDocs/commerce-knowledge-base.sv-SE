---
title: 'B2B-2674: Lägger till cachelagring i GraphQL-frågan customAttributeMetadata'
description: Använd korrigeringen B2B-2674 för att lägga till cachelagring i GraphQL-frågan customAttributeMetadata.
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: a4efb268-f811-41f2-a788-a8cfc3016f61
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# B2B-2674: Lägger till cachelagring i `customAttributeMetadata` GraphQL query

B2B-2674-korrigeringen ger cachningsfunktioner för `customAttributeMetadata` GraphQL-frågor. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 är installerat. Korrigerings-ID är B2B-2674. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7-beta1.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`customAttributeMetadata` GraphQL-frågan är inte cachelagrad.

<u>Förutsättningar</u>:

* Servern pekar på [!DNL Varnish] proxera till Adobe Commerce backend.
* Konfigurationsinställning `system/full_page_cache/caching_application` är inställd på *2* ([!DNL Varnish]) eller gå till Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > och ange [!DNL Varnish].

När korrigeringen har installerats utför du följande steg för att se till att det nu finns möjlighet till cachelagring:

1. Skicka `GET` begära att GraphQL-frågan som listas ovan görs med hjälp av valfria fält.
1. Skicka om begäran utan att göra några ändringar. Du kommer att märka att den går mycket snabbare. Observera att begäran inte skickas till backend-objektet, men att den hanteras fullständigt av [!DNL Varnish] som en cacheträff.
1. Om ytterligare korrektur krävs kan du kommentera bort `X-Magento-Debug` finns i vår [VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239)starta om [!DNL Varnish] och kör stegen ovan igen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
