---
title: 'ACSD-48587: produktwidgeten fungerar inte med SKU:er som innehåller HTML-tecken'
description: Använd patchen ACSD-48587 för att åtgärda Adobe Commerce-problemet där HTML-specialtecken i matchningsreglerna för produktwidgeten förhindrar att de visar matchande produkter.
exl-id: 9f8f436c-f3ef-4510-a941-12f701e7524e
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48587: produktwidgeten fungerar inte med SKU:er som innehåller HTML-tecken

Korrigeringen ACSD-48587 åtgärdar ett problem där HTML-specialtecken i matchningsreglerna för produktwidgetar förhindrar att de visar matchande produkter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 är installerat. Korrigerings-ID är ACSD-48587. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktwidgeten fungerar inte med SKU som innehåller *&quot;&amp;&quot;* symboler.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt som innehåller *&quot;&amp;&quot;* i SKU (t.ex. s000&amp;01).
1. Redigera innehållet på en CMS-sida på sidan *Page Builder*.
1. Lägg till en produktwidget.
1. Redigera widgeten och ange **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. Ange SKU som innehåller *&quot;&amp;&quot;* i produktfältet.
1. Spara innehållet och CMS-sidan.
1. Kontrollera *CMS-sida* innehåll för *Förhandsgranskning i Page Builder* och produktbutiken.

<u>Förväntade resultat</u>:

Produkten med *&quot;&amp;&quot;* i SKU:n visas i förhandsvisningen i Page Builder och i butiken.

<u>Faktiska resultat</u>:

Produkten med *&quot;&amp;&quot;* i SKU:n inte visas i Page Builder-förhandsvisningen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
