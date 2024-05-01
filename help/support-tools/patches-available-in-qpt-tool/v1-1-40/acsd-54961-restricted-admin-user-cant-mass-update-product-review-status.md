---
title: "ACSD-54961: Begränsad administratörsanvändare kan inte massuppdatera [!UICONTROL Product Review status]"
description: Använd patchen ACSD-54961 för att åtgärda Adobe Commerce-problemet där en begränsad administratörsanvändare inte kan massera statusen för produktgranskning.
feature: Products
role: Admin, Developer
exl-id: 26c5bacd-21de-4533-a7b6-4acbacd38fec
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54961: Begränsad administratörsanvändare kan inte massuppdatera [!UICONTROL Product Review status]

Korrigeringen ACSD-54961 åtgärdar ett problem där en begränsad administratörsanvändare inte kan massuppdatera [!UICONTROL Product Review status]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 är installerat. Korrigerings-ID är ACSD-54961. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En begränsad administratörsanvändare kan inte massuppdatera [!UICONTROL Product Review status].

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en webbplats-, butik- och butiksvy.
1. Lägg till en produkt i den andra butiken och lägg sedan till en recension.
1. Skapa en begränsad administratörsanvändare med endast åtkomst till den andra butiken.
1. Logga in som begränsad administratörsanvändare och gå sedan till **[!UICONTROL  Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]** och ange **Status** till *Godkänd* eller *Väntande*.

<u>Förväntade resultat</u>:

Den begränsade administratörsanvändaren kan uppdatera granskningar med **[!UICONTROL Mass Update]** åtgärd.

<u>Faktiska resultat</u>:

Ett fel inträffar när granskningar uppdateras med **[!UICONTROL Mass Update]** åtgärd.<br>
The `var/log/exception.log` innehåller ett liknande fel:

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
