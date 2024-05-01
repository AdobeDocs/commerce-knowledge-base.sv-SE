---
title: 'ACSD-57565: Orderkontrollpanelen visar felaktig orderinformation'
description: Använd patchen ACSD-57565 för att åtgärda Adobe Commerce-problemet där orderkontrollpanelen visar felaktig orderinformation tills tidsperioden uppdateras.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 5b292fef-23f6-479f-bf76-adad53d30cf4
source-git-commit: fdf6e6e85f903a26a7b44674937ccf88ee769d06
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57565: Orderkontrollpanelen visar felaktig orderinformation

Korrigeringen ACSD-57565 åtgärdar ett problem där orderkontrollpanelen visar felaktig orderinformation tills tidsperioden uppdateras. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.48 är installerat. Patch-ID:t är ACSD-57565. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID som söknyckelord för att hitta patchen

## Problem

På orderkontrollpanelen visas felaktig orderinformation.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL dashboard charts]**.
1. Skapa en order och fakturera den.
1. Vänta i minst 24 timmar efter att ordern har skapats.
1. Kontrollera **[!UICONTROL dashboard chart]** data.
1. Anteckna antalet order.
1. Ändra tiden till *aktuell månad* och sedan ändra tillbaka till *idag*.

<u>Förväntade resultat</u>:

Instrumentpanelsdiagrammet bör alltid visa korrekt statistik.

<u>Faktiska resultat</u>:

Instrumentpanelsdiagrammet visar felaktig statistik vid första inläsningen. Diagrammets exakta statistik uppdateras efter tidsperioden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
