---
title: 'ACSD-45168: SEO-vänliga URL:er genereras inte för produkter som har attributen url_key åsidosatt'
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

Korrigeringen ACSD-45168 åtgärdar ett problem där SEO-vänliga URL:er inte genereras för produkter som har url_key-attribut åsidosatta på butiksvynivå. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 har installerats. Korrigerings-ID är ACSD-45168. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

SEO-vänliga URL:er genereras inte för produkter som har url_key-attribut åsidosatta på butiksvisningsnivå.

<u>Steg som ska återskapas</u>:

1. Ange konfigurationen enligt följande genom att gå till **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *Ja*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Ja*
1. Rensa konfigurationscachen.
1. Skapa två kategorier: [!UICONTROL Category 1] och [!UICONTROL Category 2].
1. Skapa två produkter: [!UICONTROL Product 1] i [!UICONTROL Category 1], [!UICONTROL Product 2] i [!UICONTROL Category 1].
1. Ändra omfattningen till [!UICONTROL Default Store View] för [!UICONTROL Product 1].
1. Avmarkera den valfria URL:en [!UICONTROL Key] i [!UICONTROL Search Engine Optimization].
1. Spara produkten.
1. Växla tillbaka till [!UICONTROL All Store Views].
1. Lägg till [!UICONTROL Product 1] i [!UICONTROL Category 2] och lägg till [!UICONTROL Product 2] i [!UICONTROL Category 2].
1. Kontrollera tabellen [!UICONTROL url_rewrite] eller [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Förväntade resultat</u>:

Den SEO-anpassade URL:en för [!UICONTROL Category 2] skapas för [!UICONTROL Product 1].

<u>Faktiska resultat</u>:

Den SEO-vänliga URL:en för [!UICONTROL Category 2] saknas för [!UICONTROL Product 1] eftersom URL-nyckelattributet för butiksvyn hade skrivits över.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
