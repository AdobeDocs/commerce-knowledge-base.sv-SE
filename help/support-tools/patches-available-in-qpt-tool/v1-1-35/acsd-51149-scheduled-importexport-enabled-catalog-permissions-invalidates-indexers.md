---
title: 'ACSD-51149: Schemalagd [!UICONTROL ImportExport] med aktiverade [!UICONTROL Catalog Permissions] ogiltiga indexerare'
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

Korrigeringen ACSD-51149 åtgärdar ett problem där den schemalagda [!UICONTROL ImportExport] med aktiverad [!UICONTROL Catalog Permissions] gör indexerare ogiltiga. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 har installerats. Korrigerings-ID är ACSD-51149. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL ImportExport] med aktiverad [!UICONTROL Catalog Permissions] gör indexerare ogiltiga.

<u>Steg som ska återskapas</u>:

1. Aktivera *[!UICONTROL Catalog Permissions]*.
1. Ställ in alla indexerare till *[!UICONTROL Update by Schedule]*.
1. Skapa en enkel produkt.
1. Exportera den här produkten via **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Hämta den exporterade CSV-filen och placera den i `<AC root folder>/var/import`.
1. Skapa en schemalagd produktimport med den hämtade CSV-filen.
1. Kör fullständig omindexering.
1. Kontrollera indexerarens status. Alla indexerare ska ha statusen *[!UICONTROL Ready]*.
1. Kör den skapade schemalagda importen från rutnätet.
1. Kontrollera indexerarens status igen.

<u>Förväntade resultat</u>:

Alla indexerare har statusen *[!UICONTROL Ready]*.

<u>Faktiska resultat</u>:

Vissa indexerare har statusen *[!UICONTROL Reindex Required]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
