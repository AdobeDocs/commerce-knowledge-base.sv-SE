---
title: '"ACSD-54739: *[!UICONTROL Product Stock]* status inte begärd för *[!UICONTROL Related Product Rules]*'''
description: Använd korrigeringsfilen ACSD-54739 för att åtgärda Adobe Commerce-problemet där *[!UICONTROL Product Stock]* status används inte för *[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
exl-id: 7bc106b1-2c97-46a1-8bb6-71b99511e480
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-54739: *[!UICONTROL Product stock]* status inte begärd för *[!UICONTROL Related Product Rules]*

Korrigeringen ACSD-54739 åtgärdar ett problem där *[!UICONTROL Product stock]* status har inte begärts *[!UICONTROL Related Product Rules]*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 är installerat. Korrigerings-ID är ACSD-54739. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

*[!UICONTROL Product stock]* status har inte begärts *[!UICONTROL Related Product Rules]*.

<u>Steg som ska återskapas</u>:

1. Ange **[!UICONTROL Display Out of Stock Products]** konfiguration till *Ja*.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** och ange *Ja* för kampanjregelvillkoret.
1. Skapa den relaterade produktregeln. Gå till **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Lägg till ett villkor med attributkvantitet (välj i lager/ej i lager).
1. Kontrollera produkterna i början.

<u>Förväntade resultat</u>:

Produkten i lager/utanför lager matchar *[!UICONTROL Related Product Rules]*.

<u>Faktiska resultat</u>:

Produkten i lager/utlager matchar inte *[!UICONTROL Related Product Rules]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
