---
title: 'MDVA-28191: Ingen betalningsmetod för en webbplats i Admin Create New Order'
description: Korrigeringen MDVA-28191 åtgärdar ett problem där en betalningsmetod inte läses in i Admin **Create New Order** för en webbplats, även om betalningsmetoder kan visas för andra webbplatser.  Den här korrigeringen är tillgänglig när verktyget [QPT](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) version 1.0.5 är installerat.
exl-id: 42169743-4f09-4f0a-aadd-931cccc9b467
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28191: Ingen betalningsmetod för en webbplats i Admin - Skapa ny order

Korrigeringen MDVA-28191 åtgärdar ett problem där en betalningsmetod inte läses in i administratören **Skapa ny order** för en webbplats, även om betalningsmetoder kan visas för andra webbplatser.  Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) version 1.0.5 är installerad.

## Berörda produkter och versioner

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.3 till 2.4.1 (inklusive 2.3.5-p1).

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du skapar en order från backend-objektet skapar Adobe Commerce två citattecken, den ena är inaktiv och den andra är aktiv. Men sessionen innehåller det inaktiva offert-ID:t.

<u>Steg som ska återskapas</u>

1. Gå till **Admin Panel** > **Försäljning** > **Beställningar** och klicka på **Skapa ny order** -knappen.
1. Välj den kund du vill skapa ordern för.
1. Om din butik innehåller flera vyer väljer du den butiksvy där beställningen ska placeras, på **Skapa ny order** sida för användaren som du valde.
1. Lägg till produkter från **Kundens aktiviteter** genom att klicka på **Lägg till produkter**. Bläddra nedåt på sidan för att slutföra följande avsnitt efter behov för ordningen:
   * Använd kupongkoder
   * Betalningssätt
   * Leveranssätt
   * Beställa kommentarer

<u>Förväntat resultat:</u>

Betalningsmetoder ska läsas in i Admin för alla webbplatser.

<u>Faktiskt resultat:</u>

Ingen betalningsmetod är tillgänglig (meddelandet är inte heller tillgängligt)*Ingen betalningsinformation krävs*&quot; visas) för den här webbplatsen, även om betalningsmetoder kan visas när du testar beställningar för andra webbplatser.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
