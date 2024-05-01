---
title: "ACSD-48212: produktimport tilldelar produkten fel källa"
description: Använd patchen ACSD-48212 för att åtgärda Adobe Commerce-problemet där produktimporten tilldelar produkten fel källa.
exl-id: b3426f62-f73a-4b76-8e0e-544a9133720f
feature: Admin Workspace, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48212: Produktimport tilldelar produkten fel källa

Korrigeringen ACSD-48212 åtgärdar ett problem där produkten tilldelas fel källa vid import. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 är installerat. Korrigerings-ID är ACSD-48212. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Vid import tilldelas produkten till fel källa.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär lagerkälla.
1. Skapa en produkt med enbart standardlagerkällan.
1. Exportera produkten.
1. Kör `bin/magento cron:run`.
1. Öppna **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Välj produkten i rutnätet.
1. Ta bort tilldelning från Stock med *[!UICONTROL mass action]* -menyn.
1. Kör `bin/magento cron:run`.
1. Tilldela den sekundära källan med *[!UICONTROL mass action]* -menyn.
1. Kör `bin/magento cron:run`.
1. Ta bort produkten med *[!UICONTROL mass action]* -menyn.
1. Kör `bin/magento cron:run`.
1. Importera produkten med den tidigare exporterade CSV-filen.
1. Kontrollera källtilldelningen.

<u>Förväntade resultat</u>:

Produkten är endast tilldelad standardkällan.

<u>Faktiska resultat</u>:

Produkten är tilldelad både standardkällan och den sekundära källan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
