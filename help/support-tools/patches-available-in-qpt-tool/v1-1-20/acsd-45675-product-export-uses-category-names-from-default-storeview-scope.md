---
title: 'ACSD-45675: Produktexporten använder kategorinamn från standardarkivomfånget'
description: Korrigeringen ACSD-45675 åtgärdar ett problem där produktexporten använder kategorinamn från standardbutiksvyn. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 är installerat. Korrigerings-ID är ACSD-45675. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: 9edd718e-4c0c-44dd-b802-07c9ec7c182a
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-45675: Produktexport använder kategorinamn från standardarkivomfånget

Korrigeringen ACSD-45675 åtgärdar ett problem där produktexporten använder kategorinamn från standardbutiksvyn. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 har installerats. Korrigerings-ID är ACSD-45675. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Vid produktexport används kategorinamn från standardomfånget för butiksvyn.

<u>Steg som ska återskapas</u>:

1. Skapa en anpassad butiksvy **[!UICONTROL Thai]** i huvudbutiken.
1. Använd **[!UICONTROL Thai]** som standardbutiksvy för huvudwebbplatsen.
1. Skapa följande kategoristruktur under **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Markera kategorin **[!UICONTROL Tea]** och ändra **[!UICONTROL Scope]** till **[!UICONTROL Thai]**.
1. Ange **[!UICONTROL Category Name]** som **[!UICONTROL ชาดำ]**.
1. Skapa en enkel produkt **[!UICONTROL SP001]** och tilldela kategorin **[!UICONTROL Black]**.
1. Se till att kronen inte går.
1. Gör en produktexport. Filtrera efter SKU och välj **[!UICONTROL SP001]**.
1. Kontrollera kolumnen **[!UICONTROL categories]** i den exporterade CSV-filen.

<u>Förväntade resultat</u>:

Eftersom ingen butik valdes under exporten bör du hämta en kategorisökväg som följande: *[!UICONTROL Default Category/Tea/Black]*.

<u>Faktiska resultat</u>:

Kategorisökvägen har blandade språk: *[!UICONTROL Default Category/ชาดำ/Black]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tools] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden för kvalitetspatchar.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för ditt Adobe Commerce-problem med hjälp av [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i [!DNL QPT] finns i [Patchar som är tillgängliga i  [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i guiden för verktyget för kvalitetskorrigeringar.
