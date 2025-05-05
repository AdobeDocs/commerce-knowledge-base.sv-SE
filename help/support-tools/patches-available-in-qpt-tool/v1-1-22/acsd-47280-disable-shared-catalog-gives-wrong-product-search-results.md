---
title: '[!DNL ACSD-47280]: Inaktivera delad katalog ger felaktiga produktsökresultat'
description: Använd korrigeringen  [!DNL ACSD-47280] för att korrigera och visa rätt sökresultat när funktionen för delad katalog är inaktiverad.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: Om du inaktiverar delad katalog ger det felaktiga produktsökresultat

Korrigeringen [!DNL ACSD-47280] korrigerar visningen av rätt sökresultat när funktionen [!DNL shared catalog] är inaktiverad. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 har installerats. [!DNL patch ID] är [!DNL ACSD-47280]. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd [!DNL patch ID] som söknyckelord för att hitta korrigeringen.

## Problem

Om du inaktiverar [!DNL shared catalog] får du fel sökresultat.

<u>Förutsättningar</u>:

* [!DNL B2B] moduler har installerats

<u>Steg som ska återskapas</u>:

1. Skapa en andra webbplats.
1. Tilldela en produkt till den andra webbplatsen.
1. Kontrollera produkter på den **andra webbplatsen** med [!DNL GraphQL]:

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

1. Aktivera **[!UICONTROL Shared Catalog]** som standard [!DNL scope].
1. [!DNL GraphQL]-begäran visar inte längre några produkter för den andra webbplatsen, vilket är det korrekta resultatet.
1. Gå till [!DNL scope] på den andra webbplatsen och inaktivera **[!UICONTROL Company]**.

<u>Förväntade resultat</u>:

[!DNL GraphQL]-begäran bör fortfarande visa produkter för den andra webbplatsen.

<u>Faktiska resultat</u>:

[!DNL GraphQL]-begäran visar inga produkter för den andra webbplatsen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
