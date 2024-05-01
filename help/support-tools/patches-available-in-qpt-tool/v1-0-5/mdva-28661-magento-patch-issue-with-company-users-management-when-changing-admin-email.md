---
title: 'MDVA-28661: problem med hantering av företagsanvändare vid ändring av administratörens e-post'
description: Korrigeringen MDVA-28861 åtgärdar ett problem där användaren får ett fel när han/hon ändrar administratörens e-postadress. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat. Patch ID är MDVA-28861.
exl-id: 2d6691e5-baaf-4cef-ae7e-2b6ccc7f2cd3
feature: Admin Workspace, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28661: problem med hantering av företagsanvändare vid ändring av administratörens e-post

Korrigeringen MDVA-28861 åtgärdar ett problem där användaren får ett fel när han/hon ändrar administratörens e-postadress. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat. Patch ID är MDVA-28861.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.0 till 2.4.1 (inklusive 2.3.5-p1) med B2B-tillägg

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Efter ändring av **Företagsadministratör** e-postadress, ett fel returneras och **Företag** visas inte.

<u>Steg som ska återskapas</u>:

1. Aktivera företagsfunktioner (Läs mer om det i [Installera B2B: Aktivera B2B-funktioner i Commerce Admin](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin) i vår utvecklardokumentation och skapa ett nytt företag med två användare - en administratör och två användare - alla med e-postadresser).
1. Gå till **Commerce Admin** > **Kunder** > **Företag** och öppna ditt företagskonto.
1. Öppna **Företagsadministratör** och ändra administratör till den första användaren, vilket inkluderar att ändra **Företagsadministratör** e-post till den första användarens e-postadress.
1. Gå till Adobe Commerce klientmapp och logga in som den första användaren.
1. Gå till **Företag** -avsnitt.

<u>Förväntade resultat</u>:

The **Företag** ska visas som förväntat.

<u>Faktiska resultat</u>:

The **Företag** visas inte och ett fel som liknar följande visas:

```bash
No such entity with id = 2
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.

Mer information om hur du använder funktionen hos B2B-företag finns i följande artiklar i utvecklardokumentationen:

* [Utvecklarhandbok för B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Hantera företagsroller](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Referens för konfigurationssökvägar för Adobe Commerce Enterprise B2B-tillägg](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
