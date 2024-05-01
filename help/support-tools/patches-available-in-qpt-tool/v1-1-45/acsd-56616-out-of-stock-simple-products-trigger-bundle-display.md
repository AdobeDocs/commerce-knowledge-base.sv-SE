---
title: "ACSD-56616: Visa paketerade produkter i lager vid en enkel lagerbrist"
description: Använd patchen ACSD-56616 för att åtgärda Adobe Commerce-problemet där paketerade produkter oväntat visas i butiken när alla tillhörande enkla produkter inte finns i lager.
feature: Products
role: Admin, Developer
exl-id: 6cf8e15d-38a5-42b6-aee7-67410b501404
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616: Visa butiker för paketerade produkter vid en enkel lagerbrist.

Korrigeringen ACSD-56616 åtgärdar ett problem där paketerade produkter oväntat visas i butiken när alla tillhörande enkla produkter inte finns i lager. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 är installerat. Korrigerings-ID är ACSD-56616. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felaktig butiksvisning av paketerade produkter vid en enkel lagerbrist.

<u>Steg som ska återskapas</u>:

1. Skapa en ny webbplats/butik/butik.
1. Skapa en ny källa.
1. Skapa ett nytt arkiv och tilldela det till den nyligen skapade webbplatsen.
1. Konfigurera indexerare att uppdatera enligt schema.
1. Generera två enkla produkter, S1 (kvantitet = 1) och S2 (kvantitet = 1), och tilldela dem till den nya Stock-webbplatsen och den nya webbplatsen.
1. Skapa *bundlade1* produkten och koppla den till en ny webbplats, placera den i en kategori *CAT*.
1. Definiera två obligatoriska listrutealternativ och länka enkla produkter *S1* till alternativ1 och *S2* till alternativ2.
1. Spara produkterna.
1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** och aktivera *Lägg till butikskod i URL* = *Ja*.
1. Öppna butiken och köp den paketerade produkten.
1. Kör cron två gånger.
1. Återgå till *CAT* kategori.

<u>Förväntade resultat</u>:

The *bundle1* produkten är inte i lager.

<u>Faktiska resultat</u>:

The *bundle1* produkten är synlig med pris = *$0*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
