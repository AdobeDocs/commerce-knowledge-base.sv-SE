---
title: 'ACSD-51036: Rätvillkoren vid samtidiga REST API-anrop resulterar i en överskrivning av leveransstatus'
description: Använd patchen ACSD-51036 för att åtgärda Adobe Commerce-problemet där det finns konkurrensförhållanden under samtidiga REST API-anrop, vilket resulterar i en överskrivning av leveransstatus i artikeltabellen.
exl-id: 12d90de7-fe5c-4fcc-b84a-d420dcd871ca
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-51036: Utrymmesvillkor vid samtidiga REST API-anrop resulterar i en överskrivning av leveransstatus i artikelordningsregistret

Korrigeringen ACSD-51036 åtgärdar ett problem där tävlingsvillkoren under samtidiga REST API-anrop resulterar i en överskrivning av leveransstatus i artikelordningsregistret. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.31 är installerat. Korrigerings-ID är ACSD-51036. Observera att problemet har åtgärdats i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Följevillkoren vid samtidiga REST API-anrop resulterar i en överskrivning av leveransstatus i artikelordningsregistret.

<u>Steg som ska återskapas</u>:

1. Skapa en order med två objekt.
1. Fakturaartikel A.
1. Skicka återbetalningsbegäran för artikel A via REST API samtidigt som du skickar en leveransbegäran för artikel B.
1. Gå till beställningen i **[!UICONTROL Admin Panel]**.

<u>Förväntade resultat</u>

*[!UICONTROL Shipped 1]* status ska finnas för artikel B i *[!UICONTROL Items]* ordnad tabell.

<u>Faktiska resultat</u>

*[!UICONTROL Shipped 1]* status finns inte för objekt B i *[!UICONTROL Items]* ordnad tabell.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
