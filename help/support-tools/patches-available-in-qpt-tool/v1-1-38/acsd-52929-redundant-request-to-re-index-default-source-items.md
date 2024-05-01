---
title: 'ACSD-52929: Redundant begäran om att indexera om standardkällobjekt'
description: Använd patchen ACSD-52929 för att åtgärda Adobe Commerce-problemet där det finns en redundant begäran om att indexera om standardkällartiklarna när lagerindexeraren är konfigurerad i asynkront läge.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 978fe0d0-3917-4ba2-94bb-01c607a825cc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-52929: Redundant begäran om att indexera om standardkällobjekt

Korrigeringen ACSD-52929 åtgärdar ett problem där det finns redundans av begäranden om att indexera om standardkällartiklar när lagerindexeraren har konfigurerats i asynkront läge. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.38 är installerat. Korrigerings-ID är ACSD-52929. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det finns en redundans av begäranden om att indexera om standardkällartiklar när lagerindexeraren har konfigurerats i asynkront läge.

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL RabbitMQ].
1. Aktivera asynkron omindexeringsstrategi genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** och ange **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Skapa en anpassad lagerkälla.
1. Logga in på [!DNL RabbitMQ] kontrollpanelen och gå till fliken Köer.
1. Kontrollera `inventory.indexer.sourceItem` köa och kontrollera att det inte finns några meddelanden.
1. Öppna en enkel produkt från backend-sidan och lägg till *[!UICONTROL stock only]* till den anpassade källan och spara produkten.
1. Läs in `inventory.indexer.sourceItem` i [!DNL RabbitMQ] och kontrollera sedan meddelandena.

<u>Förväntade resultat</u>:

Det finns bara ett meddelande i kön för den anpassade källan.

<u>Faktiska resultat</u>:

Två meddelanden visas i kön: ett för standardkällan och ett för den anpassade källan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
