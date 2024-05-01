---
title: "ACSD-49042: Produkt med oändlig backorder kan inte beställas från storefront"
description: Använd patchen ACSD-49042 för att åtgärda Adobe Commerce-problemet där en produkt med oändlig backorder inte kan beställas från butiken.
exl-id: b9227296-f300-447c-a241-30ccc0691c9a
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042: Produkt med oändlig backorder kan inte beställas från storefront

Korrigeringen ACSD-49042 åtgärdar ett problem där en produkt med oändlig backorder inte kan beställas från butiken. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 är installerat. Korrigerings-ID är ACSD-49042. Observera att problemet har åtgärdats i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felet inträffar när en produkt med oändlig backorder inte kan beställas från butiken.

<u>Steg som ska återskapas</u>:

1. Ange följande konfigurationsinställningar:
   * **[!UICONTROL Display Out of Stock Products]** ange till *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** ange till *[!UICONTROL Allow Qty Below 0]*.
1. Lägg till en ny **[!DNL custom stock]** och **[!DNL custom source]**.
1. Tilldela en produkt till **[!DNL custom source]** och se till att det finns ett lagernummer för den (till exempel: *10*).
1. Öppna **[!UICONTROL Advanced Inventory]**. Ange **[!UICONTROL minimum quantity]** i kundvagnen (till exempel: *160*). Kvantiteten måste ligga över lagret.
1. Gå till butiken och köp en produkt för att skapa en reservation.
1. Ändra **[!UICONTROL product quantity]** till *0*. Det viktigaste är att spara produkten från **[!DNL Admin panel]** när det finns en reservation.
1. Öppna **[!UICONTROL product page]** i butiken och försök lägga produkten i kundvagnen.

<u>Förväntade resultat</u>:

Det går att lägga produkten i vagnen eftersom restorder för en kvantitet under *0* tillåts.

<u>Faktiska resultat</u>:

Produkten visas inte vara i lager.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
