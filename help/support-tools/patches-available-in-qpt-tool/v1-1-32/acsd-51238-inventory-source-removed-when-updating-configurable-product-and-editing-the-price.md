---
title: 'ACSD-51238: Lagerkällan tas bort när en konfigurerbar produkt uppdateras och priset redigeras'
description: Använd patchen ACSD-51238 för att åtgärda Adobe Commerce-problemet där lagerkällan tas bort när en konfigurerbar produkt uppdateras och priset redigeras.
exl-id: ab2f60fd-5da3-45f7-a489-6f4f9d34e1f1
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51238: Lagerkällan tas bort när en konfigurerbar produkt uppdateras och priset ändras

Korrigeringen ACSD-51238 åtgärdar ett problem där lagerkällan tas bort när en konfigurerbar produkt uppdateras och priset redigeras. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.32 är installerat. Korrigerings-ID är ACSD-51238. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerkällan tas bort när en konfigurerbar produkt uppdateras och priset redigeras.

<u>Steg som ska återskapas</u>:

1. Installera **[!DNL Adobe Commerce]** med **[!DNL Inventory module]**
1. Gå till **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** och skapa *två källor* och *två lager*.
1. Skapa en **[!UICONTROL configurable product]** och tilldela den till **[!UICONTROL default sources]** eller **[!UICONTROL newly created sources]**.
1. Klicka på **[!UICONTROL next button]** och *spara* produkten.
1. Redigera nu samma **[!UICONTROL Configurable Product]** och klicka på **[!UICONTROL Edit Configuration]** innanför **[!UICONTROL Configuration tab]**.
1. I `Step 3: Bulk Images,Price and Quantity`, ändra `price` och lämna `Quantity` och `Images` till `Skip quantity at this time` och `Skip image uploading at this time` respektive.
1. Klicka på **[!UICONTROL next button]** och generera produkten.

<u>Förväntade resultat</u>

Kvantiteten per källa i **[!UICONTROL Configuration tab]** borde inte vara tom.

<u>Faktiska resultat</u>

Kvantiteten per källa i **[!UICONTROL Configuration tab]** är tom.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool] guide.
