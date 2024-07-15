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

Korrigeringen ACSD-57565 åtgärdar ett problem där orderkontrollpanelen visar felaktig orderinformation tills tidsperioden uppdateras. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.48 har installerats. Patch-ID:t är ACSD-57565. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID som söknyckelord för att hitta patchen

## Problem

På orderkontrollpanelen visas felaktig orderinformation.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL dashboard charts]**.
1. Skapa en order och fakturera den.
1. Vänta i minst 24 timmar efter att ordern har skapats.
1. Kontrollera **[!UICONTROL dashboard chart]**-data.
1. Anteckna antalet order.
1. Ändra tiden till den *aktuella månaden* och ändra den sedan tillbaka till *idag*.

<u>Förväntade resultat</u>:

Instrumentpanelsdiagrammet bör alltid visa korrekt statistik.

<u>Faktiska resultat</u>:

Instrumentpanelsdiagrammet visar felaktig statistik vid första inläsningen. Diagrammets exakta statistik uppdateras efter tidsperioden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
