---
title: 'ACSD-51735: Orderartikelstatus felaktigt inställd på *[!UICONTROL Ordered]* när produkten är 0'
description: Använd patchen ACSD-51735 för att åtgärda Adobe Commerce-problemet där orderobjektets status är felaktigt inställd på *[!UICONTROL Ordered]* när lagret är 0.
feature: Orders, Products
role: Admin
exl-id: c6376698-71dc-46b8-a5b2-86dc26a574ab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-51735: Orderartikelstatus är felaktigt inställd på *[!UICONTROL Ordered]* när produktlager är 0

Korrigeringen ACSD-51735 åtgärdar ett problem där orderartikelns status är felaktigt inställd på *[!UICONTROL Ordered]* när produktlagret är 0. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 är installerat. Korrigerings-ID är ACSD-50895. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Orderartikelstatus är felaktigt inställd på *[!UICONTROL Ordered]* när produktlagret är 0.

<u>Förutsättningar</u>:

* Adobe Commerce Inventory management-moduler (MSI) är installerade.
* Restorder aktiveras i **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**.

<u>Steg som ska återskapas</u>:

1. Skapa en ny aktie.
1. Skapa en ny källa.
1. Tilldela standardwebbplatsen till den nya Adobe Stock och tilldela den nya källan.
1. Skapa en ny produkt.

   * Ställ in standardkällans kvantitet till 10 och den nya källans kvantitet till 0.

1. Lägg produkten i kundvagnen på butiken.
1. Observera varningsmeddelandet vid utcheckning som anger att produkten kommer från en ny källa.
1. Beställ.
1. Öppna ordern i Admin och kontrollera restorderstatus.

<u>Förväntade resultat</u>:

Ordern visar att Kvantitet 1 är restorder.

<u>Faktiska resultat</u>:

Ordern visar att Kvantitet 1 är beställt, inte är underordnad.

>[!MORELIKETHIS]
>
>[Orderartikelstatus är felaktigt inställd på *[!UICONTROL Backordered]*](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
