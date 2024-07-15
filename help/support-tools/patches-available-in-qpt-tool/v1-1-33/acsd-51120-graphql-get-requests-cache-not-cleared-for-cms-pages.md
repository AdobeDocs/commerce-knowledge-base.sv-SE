---
title: 'ACSD-51120: Cacheminnet för GraphQL GET-begäran har inte rensats för CMS-sidor som innehåller CMS-block'
description: Använd korrigeringsfilen ACSD-51120 för att åtgärda Adobe Commerce-problemet där GraphQL GET request cache inte rensas för CMS-sidor som innehåller CMS-block.
exl-id: 22abba89-b697-45d7-972e-bf3233e5e9ec
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-51120: Cacheminnet för GraphQL GET-begäran har inte rensats för CMS-sidor som innehåller CMS-block

Korrigeringen ACSD-51120 åtgärdar ett problem där cache-minnet för GraphQL GET-begäran inte rensas för CMS-sidor som innehåller CMS-block som uppdateras via en mellanlagringsuppdatering. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 har installerats. Korrigerings-ID är ACSD-51120. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Cacheminnet för begäran om GraphQL GET rensas inte för CMS-sidor som innehåller CMS-block som uppdateras via en mellanlagringsuppdatering.

<u>Steg som ska återskapas</u>:

1. Skapa ett CMS-block.
1. Inkludera CMS-blocket på en CMS-sida med [!DNL Page Builder].
1. Hämta CMS-sidan med den angivna GraphQL-frågan med hjälp av en GET-begäran:

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. Kontrollera att GraphQL-svaret är cachelagrat i [!DNL Varnish].
1. Skapa en schemalagd uppdatering för blocket.
1. Vänta tills den schemalagda uppdateringen har tillämpats och kör kron-jobbet för att tillämpa den schemalagda uppdateringen.
1. Hämta CMS-sidan igen med den angivna GraphQL-frågan med hjälp av en GET-begäran.

<u>Förväntade resultat</u>:

Svaret visar det uppdaterade innehållet.

<u>Faktiska resultat</u>:

Svaret visar fortfarande det gamla innehållet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
