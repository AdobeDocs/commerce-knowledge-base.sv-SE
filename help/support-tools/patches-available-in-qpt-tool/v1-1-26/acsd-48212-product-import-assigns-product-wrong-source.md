---
title: 'ACSD-48212: Produktimport tilldelar produkten fel källa'
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

Korrigeringen ACSD-48212 åtgärdar ett problem där produkten tilldelas fel källa vid import. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 har installerats. Korrigerings-ID är ACSD-48212. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Vid import tilldelas produkten till fel källa.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär lagerkälla.
1. Skapa en produkt med enbart standardlagerkällan.
1. Exportera produkten.
1. Kör `bin/magento cron:run`.
1. Öppna **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Välj produkten i rutnätet.
1. Ta bort tilldelningen för Stock med menyn *[!UICONTROL mass action]*.
1. Kör `bin/magento cron:run`.
1. Tilldela den sekundära källan via menyn *[!UICONTROL mass action]*.
1. Kör `bin/magento cron:run`.
1. Ta bort produkten från menyn *[!UICONTROL mass action]*.
1. Kör `bin/magento cron:run`.
1. Importera produkten med den tidigare exporterade CSV-filen.
1. Kontrollera källtilldelningen.

<u>Förväntade resultat</u>:

Produkten är endast tilldelad standardkällan.

<u>Faktiska resultat</u>:

Produkten är tilldelad både standardkällan och den sekundära källan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
