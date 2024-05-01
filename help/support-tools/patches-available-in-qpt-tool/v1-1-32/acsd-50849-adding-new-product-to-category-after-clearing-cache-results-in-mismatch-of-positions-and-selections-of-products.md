---
title: '''ACSD-50849: Om du lägger till en ny produkt efter att cacheminnet rensats blir matchningsfelet'
description: Använd korrigeringsfilen ACSD-50849 för att korrigera Adobe Commerce-problemet där en ny produkt läggs till i kategorin efter att cacheminnet rensats resulterar i en felmatchning av positioner och urval av befintliga produkter.
feature: Cache, Categories, Products
role: Admin
exl-id: 3c797bf4-45da-4500-8c06-8c1007249738
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-50849: Om du lägger till en ny produkt efter att cacheminnet rensats blir matchningsfelet felaktig

Korrigeringen ACSD-50849 åtgärdar ett problem där en ny produkt läggs till i kategorin efter att cacheminnet rensats, vilket resulterar i en felmatchning av positioner och val för befintliga produkter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) QPT 1.1.32 är installerat. Korrigerings-ID är ACSD-50849. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du lägger till en ny produkt i kategorin efter att du rensat cacheminnet skapas en felmatchning av positioner och val för de befintliga produkterna.

<u>Steg som ska återskapas</u>:

1. Skapa två produkter.
1. Tilldela en produkt till en kategori.
1. Öppna kategorin från administratören.
1. Rensa cachen `bin/magento cache:flush`.
1. Lägg till den andra produkten i kategorin.

<u>Förväntade resultat</u>:

Befintliga produkter som tilldelats i kategorin tas inte bort automatiskt.

<u>Faktiska resultat</u>:

Den första (befintliga) produkten tas bort automatiskt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
