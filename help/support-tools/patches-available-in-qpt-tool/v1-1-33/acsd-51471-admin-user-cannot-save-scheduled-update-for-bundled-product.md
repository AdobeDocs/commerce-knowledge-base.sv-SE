---
title: 'ACSD-51471: Administratörsanvändaren kan inte spara schemalagd uppdatering för paketerad produkt'
description: Använd patchen ACSD-51471 för att åtgärda Adobe Commerce-problemet där en administratörsanvändare inte kan spara en schemalagd uppdatering för en paketerad produkt som använder en enkel produkt med en schemalagd uppdatering.
exl-id: 7d80aef0-8505-4491-bde3-5b1a30b840f6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-51471: Administratörsanvändaren kan inte spara schemalagd uppdatering för paketerad produkt

Korrigeringen ACSD-51471 åtgärdar ett problem där en administratörsanvändare inte kan spara en schemalagd uppdatering för en paketerad produkt som använder en enkel produkt med en schemalagd uppdatering. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 är installerat. Korrigerings-ID är ACSD-51471. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändare kan inte spara en schemalagd uppdatering för en paketerad produkt som använder en enkel produkt som själv har en schemalagd uppdatering.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Lägg till en schemalagd uppdatering för den enkla produkten med endast *Startdatum* och nej *Slutdatum*.
1. När uppdateringen har installerats ändrar du SKU för produkten.
1. Skapa en paketerad produkt och lägg till den enkla produkten som skapats i steg 1 som en underordnad produkt.
1. Skapa en schemalagd uppdatering för den paketerade produkten för att aktivera den paketerade produkten. Ange båda *Startdatum* och *Slutdatum* för den schemalagda uppdateringen.
1. Spara den schemalagda uppdateringen.

<u>Förväntade resultat</u>:

Den schemalagda uppdateringen har sparats.

<u>Faktiska resultat</u>:

Följande fel inträffar när den schemalagda uppdateringen sparas: *Den begärda produkten finns inte. Kontrollera produkten och försök igen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
