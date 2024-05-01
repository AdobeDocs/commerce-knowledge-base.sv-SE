---
title: "ACSD-47875: Det går inte att lägga till produkten i varukorgen för butiksvyn med lagerhantering"
description: Använd patchen ACSD-47875 för att åtgärda Adobe Commerce-problemet där en produkt inte kan läggas till i kundvagnen från Admin för ett visst butiksvy med lagerhantering.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: fa5ecd65-704f-49bd-b3cc-3d60ff7e1dce
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-47875: Det går inte att lägga till produkten i varukorgen för butiksvyn med lagerhantering

Korrigeringen ACSD-47875 åtgärdar ett problem där en produkt inte kan läggas till i en kundvagn från administratören för ett visst butiksvy med lagerhantering. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.36 är installerat. Korrigerings-ID är ACSD-47875. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändare kan inte lägga till en produkt i kundvagnen med **[!UICONTROL Manage Shopping Cart]** i Admin för en viss butiksvy där MSI är installerat.

<u>Förutsättningar</u>:

[!DNL Adobe Commerce Inventory Management (MSI)] moduler installeras och aktiveras.

<u>Steg som ska återskapas</u>:

1. Skapa en webbplats, en butik och en butiksvy.
1. Skapa en annan källa än *Standard*.
1. Skapa ett nytt arkiv och tilldela det till den nya webbplatsen och den nya källan.
1. Skapa en ny kund för den nya webbplatsen.
1. Tilldela bara en produkt till den nya webbplatsen. Ta bort tilldelning från standardwebbplatsen.

   * Tilldela den nya källan och ange kvantitet *över 0* för den nya källan och *0* för standardkällan.

1. Gå till **[!UICONTROL Customer Edit]** i Admin. Klicka på **[!UICONTROL Manage Shopping Cart]**.
1. Ändra butiksvyns omfattning till den nya butiksvyn.
1. Gå till **[!UICONTROL Products]** och sök efter produkten.
1. Välj produkten och klicka på **[!UICONTROL Add selections to my cart]**.

<u>Förväntade resultat</u>:

Produkten läggs i varukorgen.

<u>Faktiska resultat</u>:

* Följande fel genereras: *Produkten som du försöker lägga till är inte tillgänglig.*
* Produkten läggs inte till i kundvagnen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
