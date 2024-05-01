---
title: '''ACSD-51984: Omarkerad [!UICONTROL Use Default Value] och värden som inte är standardvärden för produktfält sparas inte för den andra webbplatsen, butiken och butiksvyn'
description: Använd korrigeringen ACSD-51984 för att åtgärda Adobe Commerce-problemet där den avmarkerade [!UICONTROL Use Default Value] och värden som inte är standardvärden för produktfält sparas inte för den andra webbplatsen, butiken och butiksvyn.
feature: Products
role: Admin
exl-id: 1f45c700-dd27-4a69-8634-9c0aa131d197
source-git-commit: f42fcacbe3b7174b2a3571afe80f5eedb8e9aa75
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-51984: Omarkerad *[!UICONTROL Use Default Value]* och icke-standardvärden för produktfält sparas inte

>[!NOTE]
>
>Den här korrigeringen är inaktuell och har ersatts av [ACSD-54776](/help/support-tools/patches-available-in-qpt-tool/v1-1-39/acsd-54776-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) patch som lagts till i 1.1.39 QPT-versionen.

Korrigeringen ACSD-51984 åtgärdar ett problem där den avmarkerade **[!UICONTROL Use Default Value]** och värden som inte är standardvärden för produktfält sparas inte för den andra webbplatsen, butiken och butiksvyn. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 är installerat. Korrigerings-ID är ACSD-51984. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Omarkerad *[!UICONTROL Use Default Value]* och värden som inte är standardvärden för produktfält sparas inte för den andra webbplatsen, butiken och butiksvyn.

<u>Steg som ska återskapas</u>:

1. Gå till serverdelen och navigera till **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** och skapa en ny webbplats, butik och butiksvy.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, skapa en enkel produkt och spara den och tilldela produkten till båda webbplatserna via **[!UICONTROL Product in Websites]**.
1. Ändra omfattningen till den nya butiksvyn från steg 2.
1. Gå till **[!UICONTROL Search Engine Optimization]** och avmarkera **[!UICONTROL Use Default Value]** kryssrutor för [!UICONTROL Meta Title], [!UICONTROL Meta Keywords]och [!UICONTROL Meta Description].
1. Rensa texten från fälten: *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* och *[!UICONTROL Meta Description]* och klicka **[!UICONTROL Save]**.
1. Gå till **[!UICONTROL Search Engine Optimization]** igen.

<u>Förväntade resultat</u>

Värdena för fälten och kryssrutorna sparas.

<u>Faktiska resultat</u>

Värdena för fälten och kryssrutorna sparas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool] guide.