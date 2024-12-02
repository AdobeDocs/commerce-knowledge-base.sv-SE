---
title: 'ACSD-51238: Lagerkällan tas bort när en konfigurerbar produkt uppdateras och priset ändras'
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

Korrigeringen ACSD-51238 åtgärdar ett problem där lagerkällan tas bort när en konfigurerbar produkt uppdateras och priset redigeras. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.32 har installerats. Korrigerings-ID är ACSD-51238. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerkällan tas bort när en konfigurerbar produkt uppdateras och priset redigeras.

<u>Steg som ska återskapas</u>:

1. Installera **[!DNL Adobe Commerce]** med **[!DNL Inventory module]**
1. Gå till **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** och skapa *två källor* och *två lager*.
1. Skapa en **[!UICONTROL configurable product]** och tilldela den till **[!UICONTROL default sources]** eller **[!UICONTROL newly created sources]**.
1. Klicka på **[!UICONTROL next button]** och *spara* produkten.
1. Redigera nu samma **[!UICONTROL Configurable Product]** och klicka på **[!UICONTROL Edit Configuration]** inuti **[!UICONTROL Configuration tab]**.
1. I `Step 3: Bulk Images,Price and Quantity` ändrar du `price` och låter `Quantity` och `Images` vara `Skip quantity at this time` respektive `Skip image uploading at this time`.
1. Klicka på **[!UICONTROL next button]** och generera produkten.

<u>Förväntade resultat</u>

Kvantiteten per källa i **[!UICONTROL Configuration tab]** får inte vara tom.

<u>Faktiska resultat</u>

Kvantiteten per källa i **[!UICONTROL Configuration tab]** är tom.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool]-handboken.
