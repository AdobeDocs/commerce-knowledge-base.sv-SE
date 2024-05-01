---
title: 'ACSD-51645: Sparar en ny kundprisregel om tillägget Magento_OfflineShipping är inaktiverat'
description: Använd patchen ACSD-51645 för att åtgärda Adobe Commerce-problemet när ett fel inträffar när en ny kundprisregel sparas om tillägget Magento_OfflineShipping är inaktiverat.
exl-id: 301086bb-7aab-4e74-93e6-9080eebcb026
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-51645: Spara en ny kundprisregel om tillägget Magento_OfflineShipping är inaktiverat

Korrigeringen ACSD-51645 åtgärdar ett problem där ett fel inträffar när en ny kundprisregel sparas om tillägget Magento_OfflineShipping är inaktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 är installerat. Korrigerings-ID är ACSD-51645. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel uppstod när en ny kundprisregel sparades om tillägget `Magento_OfflineShipping` är inaktiverat.

<u>Steg som ska återskapas</u>:

1. Inaktivera `Magento_OfflineShipping` -modul.
1. Logga in på **Administratör**.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**.
1. Skapa ett nytt **[!UICONTROL Cart Price Rule]**.
1. Fyll i obligatoriska fält.
1. Spara **[!UICONTROL Cart Price Rule]**.

<u>Förväntade resultat</u>:

Kundprisregeln har sparats.

<u>Faktiska resultat</u>:

Följande fel inträffar:
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool] guide.
