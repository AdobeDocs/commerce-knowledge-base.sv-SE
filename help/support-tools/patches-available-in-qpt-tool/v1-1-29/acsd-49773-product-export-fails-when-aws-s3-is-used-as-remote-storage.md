---
title: 'ACSD-49773: Produktexporten misslyckas när AWS S3 används som fjärrlagring'
description: Använd patchen ACSD-49773 för att åtgärda problemet med Adobe Commerce där produktexporten misslyckas när AWS S3 används som fjärrlagring.
exl-id: 5ef853c3-8080-4403-836b-6fff93ec71c6
feature: Data Import/Export, Iaas, Products, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-49773: Produktexport misslyckas när AWS S3 används som fjärrlagring

Korrigeringen ACSD-49773 åtgärdar ett problem där produktexporten misslyckas när AWS S3 används som fjärrlagring. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 är installerat. Korrigerings-ID är ACSD-49773. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktexporten misslyckas när AWS S3 används som fjärrlagring.

<u>Steg som ska återskapas</u>:

1. Installera en stor dataprofil.
1. Skapa ett AWS-konto och konfigurera en S3-bucket och en IAM-användare.
1. Uppdatera `app/etc/env.php` med konfigurationerna.
1. Kör `bin/magento setup:upgrade`.
1. Gå till backend och utför en fullständig produktexport.
1. Övervaka kömeddelandets status från `[queue_message_status]` tabell.
1. Kontrollera systemloggarna.

<u>Förväntade resultat</u>:

Produktexporten avslutas utan fel.

<u>Faktiska resultat</u>:

Ett fel loggas i systemloggarna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
