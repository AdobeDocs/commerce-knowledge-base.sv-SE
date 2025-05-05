---
title: 'ACSD-52095: Hantera lagervärde är fel vid export av CSV'
description: Använd korrigeringsfilen ACSD-52095 för att åtgärda problemet med Adobe Commerce där produkthantering för Stock-värdet är fel vid export av CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095: Värdet [!UICONTROL Manage Stock] är fel vid export av CSV

ACSD-52095-korrigeringen åtgärdar ett problem där värdet för produkten `manage_stock` är fel vid export av CSV. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 har installerats. Korrigerings-ID är ACSD-52095. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Värdet `manage_stock` har felaktigt angetts till 0 i CSV-filen efter produktexporten.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** och ange **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Skapa en ny produkt och spara den.
1. Gå till **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Välj *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* och exportera produkterna.
1. Kontrollera den genererade CSV-filen: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Gå igen till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** och ange **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Gå till **System** > **Exportera**.
Välj *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Kontrollera den genererade CSV-filen: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Öppna produkten i Admin, gå till **[!UICONTROL Advanced Inventory]** och kontrollera värdet för **[!UICONTROL Manage Stock]**.

<u>Förväntade resultat</u>

Värdet **[!UICONTROL Manage Stock]** är *1* när det är aktiverat för produkterna.

<u>Faktiska resultat</u>

Värdet **[!UICONTROL Manage Stock]** är *0* när det är aktiverat för produkterna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE>) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE>) i [!DNL Quality Patches Tool]-handboken.
