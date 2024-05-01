---
title: 'MDVA-31295: Lojalitetspunkter för partiella order'
description: MDVA-31295-korrigeringen åtgärdar ett problem där belöningspoäng inte beräknas korrekt när en delorder slutförs och artiklarna beskattas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 10e8a3a9-bfab-4256-b772-fd64e8885da3
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31295: Lojalitetspunkter på partiella order

MDVA-31295-korrigeringen åtgärdar ett problem där belöningspoäng inte beräknas korrekt när en delorder slutförs och artiklarna beskattas. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce lokal 2.3.0

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Belöningar tillämpas inte på kundkonton när ordern är slutförd (delvis levererad) och artiklarna beskattas. När artiklarna inte beskattas läggs belöningarna till i kundens konton.

<u>Steg som ska återskapas</u>:

1. Logga in i butiken som kund.
1. Lägg två produkter i kundvagnen.
1. Gå till kassan, ange leveransadress och beställ.
1. Gå till den senast placerade ordern i administratören.
1. Klicka **Faktura** och ange **Ant att fakturera** till 0 för ett av objekten och klicka på **Uppdatera kvantitet**. Skicka faktura.
1. Klicka på Leverera och ange **Antal att leverera** till 0 för artikeln som inte fakturerades. Klicka **Skicka utleverans**.
1. Klicka på Avbryt beställning. Statusen anges som Fullständig.
1. Gå till Admin **Kunder** > Välj kundköp som gjorts före > **Belöningspunkter** > **Historik för belöningspunkter**.
1. Kontrollera intjänade belöningspoäng för den placerade ordern.

<u>Förväntade resultat</u>:

Belöningspoängen bör beräknas för skattepliktiga order när en partiell order har slutförts.

<u>Faktiska resultat</u>:

Belöningspoäng beräknas inte för en beskattningsbar order när en partiell order är slutförd.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
