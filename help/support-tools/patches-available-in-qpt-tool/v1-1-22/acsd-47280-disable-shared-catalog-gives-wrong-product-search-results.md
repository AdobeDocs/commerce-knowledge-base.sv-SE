---
title: '''[!DNL ACSD-47280]: Inaktivera delad katalog ger fel produktsökresultat'
description: Använd [!DNL ACSD-47280] korrigering för att visa rätt sökresultat när funktionen för delad katalog är inaktiverad.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: Inaktivering av delad katalog ger felaktiga produktsökresultat

The [!DNL ACSD-47280] korrigeringsfilen korrigerar visningen av rätt sökresultat när [!DNL shared catalog] funktionen är inaktiverad. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 är installerat. The [!DNL patch ID] är [!DNL ACSD-47280]. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd [!DNL patch ID] som ett söknyckelord för att hitta korrigeringen.

## Problem

Inaktiverar [!DNL shared catalog] ger fel produktsökresultat.

<u>Förutsättningar</u>:

* [!DNL B2B] installerade moduler

<u>Steg som ska återskapas</u>:

1. Skapa en andra webbplats.
1. Tilldela en produkt till den andra webbplatsen.
1. Kontrollera produkter på **andra webbplatsen** använda [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. Aktivera **[!UICONTROL Shared Catalog]** på standard [!DNL scope].
1. The [!DNL GraphQL] -begäran visar inte längre några produkter för den andra webbplatsen, vilket är rätt resultat.
1. Gå till [!DNL scope] av den andra webbplatsen och inaktivera **[!UICONTROL Company]**.

<u>Förväntade resultat</u>:

The [!DNL GraphQL] begäran ändå bör visa produkter för den andra webbplatsen.

<u>Faktiska resultat</u>:

The [!DNL GraphQL] begäran inte visar några produkter för den andra webbplatsen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
