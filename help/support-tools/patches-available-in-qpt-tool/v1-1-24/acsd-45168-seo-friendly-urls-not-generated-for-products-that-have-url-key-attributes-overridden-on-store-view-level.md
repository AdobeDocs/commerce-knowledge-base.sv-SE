---
title: 'ACSD-45168: SEO-vänliga URL:er genereras inte för produkter som har åsidosatt attributen url_key'
description: Använd patchen ACSD-45168 för att åtgärda Adobe Commerce-problemet där SEO-vänliga URL:er inte genereras för produkter som har attributen url_key åsidosatt på butiksvisningsnivå.
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168: SEO-vänliga URL:er genereras inte för produkter som har attributen url_key åsidosatt

Korrigeringen ACSD-45168 åtgärdar ett problem där SEO-vänliga URL:er inte genereras för produkter som har url_key-attribut åsidosatta på butiksvynivå. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 är installerat. Korrigerings-ID är ACSD-45168. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

SEO-vänliga URL:er genereras inte för produkter som har url_key-attribut åsidosatta på butiksvisningsnivå.

<u>Steg som ska återskapas</u>:

1. Ange konfigurationen enligt följande genom att gå till **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *Ja*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Ja*
1. Rensa konfigurationscachen.
1. Skapa två kategorier: [!UICONTROL Category 1] och [!UICONTROL Category 2].
1. Skapa två produkter: [!UICONTROL Product 1] in [!UICONTROL Category 1], [!UICONTROL Product 2] in [!UICONTROL Category 1].
1. Ändra omfånget till [!UICONTROL Default Store View] for [!UICONTROL Product 1].
1. Avmarkera den valfria URL:en [!UICONTROL Key] in [!UICONTROL Search Engine Optimization].
1. Spara produkten.
1. Växla tillbaka till [!UICONTROL All Store Views].
1. Lägg till [!UICONTROL Product 1] till [!UICONTROL Category 2]och lägga till [!UICONTROL Product 2] till [!UICONTROL Category 2].
1. Kontrollera [!UICONTROL url_rewrite] tabell eller [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Förväntade resultat</u>:

Den SEO-vänliga URL:en för [!UICONTROL Category 2] skapas för [!UICONTROL Product 1].

<u>Faktiska resultat</u>:

Den SEO-vänliga URL:en för [!UICONTROL Category 2] saknas för [!UICONTROL Product 1] eftersom URL-nyckelattributet för butiksvyn hade skrivits över.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
