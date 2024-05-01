---
title: '"ACSD-54965: [!UICONTROL Visual Merchandising] rutnätet visar inte rätt Stock'''
description: Använd korrigeringsfilen ACSD-54965 för att åtgärda Adobe Commerce-problemet där [!UICONTROL Visual Merchandising] Rutnätet visar inte rätt lager när en produkt tilldelas en anpassad Stock.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: 13d98f55-ca2c-4064-b66f-ab2cdeb37382
source-git-commit: 4f05117aa42dec1f56e4986ffd22d1a68bf5cea2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965: [!UICONTROL Visual Merchandising] rutnätet visar inte rätt resurs

Korrigeringen ACSD-54965 åtgärdar ett problem där [!UICONTROL Visual Merchandising] Rutnätet visar inte rätt lager när en produkt tilldelas en anpassad Stock. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 är installerat. Korrigerings-ID är ACSD-54965. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The [!UICONTROL Visual Merchandising] Rutnätet visar inte rätt lager när en produkt tilldelas en anpassad Stock.

<u>Steg som ska återskapas</u>:

1. Skapa en ny källa.
1. Skapa en ny aktie.
1. Skapa två produkter:
   * En produkt som endast innehåller det anpassade lagret.
   * En produkt med endast standardlagret.
1. Lägg till de här produkterna i en kategori.
1. Gå till [!UICONTROL visual Merchandising] rutnät (*[!UICONTROL Products in Category]*).

<u>Faktiska resultat</u>:

I *[!UICONTROL All Store Views]* omfång, produkten med anpassade lager visar inte någon kvantitet. Det är bara när *[!UICONTROL Default Store View]* omfånget har valts. Det anpassade lagret visar produktkvantiteten.

<u>Förväntade resultat</u>:

Rutnätet visar all stockinformation om omfattningen är *[!UICONTROL All Store Views]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
