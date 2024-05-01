---
title: '''ACSD-51149: Schemalagd [!UICONTROL ImportExport] med aktiverad [!UICONTROL Catalog Permissions] gör indexerare ogiltiga'
description: Använd korrigeringsfilen ACSD-51149 för att åtgärda prestandaproblemet i Adobe Commerce där den schemalagda [!UICONTROL ImportExport] med aktiverad [!UICONTROL Catalog Permissions] gör indexerare ogiltiga.
feature: Cache, Data Import/Export
role: Admin
exl-id: 3a26f4be-8e52-407d-bb25-2841458f3aa5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51149: Schemalagd [!UICONTROL ImportExport] med aktiverad [!UICONTROL Catalog Permissions] gör indexerare ogiltiga

Korrigeringen ACSD-51149 åtgärdar ett problem där den schemalagda [!UICONTROL ImportExport] med aktiverad [!UICONTROL Catalog Permissions] gör indexerare ogiltiga. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 är installerat. Korrigerings-ID är ACSD-51149. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Schemalagd [!UICONTROL ImportExport] med aktiverad [!UICONTROL Catalog Permissions] gör indexerare ogiltiga.

<u>Steg som ska återskapas</u>:

1. Aktivera *[!UICONTROL Catalog Permissions]*.
1. Ställ in alla indexerare på *[!UICONTROL Update by Schedule]*.
1. Skapa en enkel produkt.
1. Exportera den här produkten via **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Hämta den exporterade CSV-filen och placera den i `<AC root folder>/var/import`.
1. Skapa en schemalagd produktimport med den hämtade CSV-filen.
1. Kör fullständig omindexering.
1. Kontrollera indexerarens status. Alla indexerare ska vara i *[!UICONTROL Ready]* status.
1. Kör den skapade schemalagda importen från rutnätet.
1. Kontrollera indexerarens status igen.

<u>Förväntade resultat</u>:

Alla indexerare finns i *[!UICONTROL Ready]* status.

<u>Faktiska resultat</u>:

Vissa av indexerarna finns i *[!UICONTROL Reindex Required]* status.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
