---
title: 'ACSD-50367: Kundadressexport fungerar inte med flervalsattribut'
description: Använd patchen ACSD-50367 för att åtgärda Adobe Commerce-problemet där kundadressexporten inte fungerar när ett flervalsattribut (*`Customer Address`** utan värden skapas.
exl-id: 688831d4-b49e-48fa-b4db-1328cda09a2b
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-50367: Kundadressexport fungerar inte

Korrigeringsfilen ACSD-50367 åtgärdar ett problem där kundadressexporten inte fungerar när flera användare väljer den **`Customer Address`** utan värden skapas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 är installerat. Korrigerings-ID är ACSD-50367. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundadressexport fungerar inte när flera användare väljs **`Customer Address`** utan värden skapas.

<u>Förutsättningar</u>:

Skapa en kund med en adress.

<u>Steg som ska återskapas</u>:

1. Skapa ett flerval **`Customer Address`** attribute in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** och markera **`Customer Address`** entitetstyp.
1. Exportera kundadresserna. Du kommer att se att inget exporteras.
1. Ta bort flermarkeringen **`Customer Address`** och exportera kundadresserna igen. Den här gången genereras adressernas CSV-fil.

<u>Förväntade resultat</u>:

Kundadresserna kan exporteras som en CSV-fil när du väljer flera **`Customer Address`** attribut skapas.

<u>Faktiska resultat</u>:

Det går inte att exportera kundadresserna som en CSV-fil när du väljer flera **`Customer Address`** attribut skapas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
