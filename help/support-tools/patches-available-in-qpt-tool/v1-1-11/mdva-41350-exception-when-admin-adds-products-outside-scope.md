---
title: 'MDVA-41350: Undantag när administratören lägger till produkter utanför sin åtkomst'
description: Korrigeringen MDVA-41350 åtgärdar ett problem där ett undantagsfel inträffar i stället för ett meddelande om begränsad åtkomst när en administratörsanvändare lägger till en produkt i ordningen från SKU som de inte har tillgång till. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 är installerat. Korrigerings-ID är MDVA-41350. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 3a96d029-5350-4dd6-aad3-2f2cdd5e65ac
feature: Admin Workspace, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-41350: Undantag när administratören lägger till produkter utanför sin åtkomst

Korrigeringen MDVA-41350 åtgärdar ett problem där ett undantagsfel inträffar i stället för ett meddelande om begränsad åtkomst när en administratörsanvändare lägger till en produkt i ordningen från SKU som de inte har tillgång till. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 är installerat. Korrigerings-ID är MDVA-41350. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När en administratörsanvändare med begränsad åtkomst lägger till en produkt från SKU utanför sin åtkomst i ordern, inträffar ett undantag i stället för ett meddelande som meddelar användaren om deras begränsade åtkomst.

<u>Steg som ska återskapas</u>:

1. Logga in i administratören som användare med tillgång till endast en specifik webbplats.
1. Gå till **Försäljning** > **Beställningar** och klicka **Skapa ny order**.
1. Välj kund och butiksvy.
1. Klicka på **Lägg till produkter efter SKU**.
1. Sök efter en SKU som inte är tilldelad någon webbplats eller som inte är tilldelad den webbplats som du har åtkomst till.
1. Klicka **Lägg till i order**.

<u>Förväntade resultat</u>:

Ett felmeddelande visas.

<u>Faktiska resultat</u>:

Ett undantag inträffar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
