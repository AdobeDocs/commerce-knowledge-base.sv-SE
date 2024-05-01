---
title: '"ACSD-46865: [!UICONTROL shipment] och [!UICONTROL credit memo] inte ifylld när [!UICONTROL asynchronous indexing] är aktiverat'
description: Åtgärda Adobe Commerce-problemet med korrigeringen ACSD-46865 där [!UICONTROL shipment] och [!UICONTROL credit memo] stödraster fylls inte i när [!UICONTROL asynchronous indexing] är aktiverat.
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] och [!UICONTROL credit memo] inte ifylld när [!UICONTROL asynchronous indexing] är aktiverat

Korrigeringen ACSD-46865 åtgärdar ett problem där [!UICONTROL shipment] och [!UICONTROL credit memo] stödraster fylls inte i när [!UICONTROL asynchronous indexing] är aktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 är installerat. Korrigerings-ID är ACSD-46865. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL Shipment] och [!UICONTROL credit memo] stödraster fylls inte i när [!UICONTROL asynchronous indexing] är aktiverat.

<u>Steg som ska återskapas</u>:

1. I [!DNL Commerce] Admin, gå till **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *JA*.
2. Återgå till **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Rensa konfigurationscachen.
4. Gör en ny gästbeställning av en enkel produkt.
5. Spring cron.
6. Öppna ordern i [!UICONTROL Commerce] Administratör genom att gå till **[!UICONTROL Sales]** > **[!UICONTROL Orders]** och generera en faktura och en kreditnota.
7. Flytta ordningen till [!UICONTROL Archive].
8. Skapa en ny order för en enkel produkt.
9. Spring cron.
10. Gå till den nya ordern och generera en ny leverans, en faktura och en kreditnota.
11. Spring cron.
12. Kontrollera [!UICONTROL shipments], [!UICONTROL invoices]och [!UICONTROL credit memo] rutnät i administratören.

<u>Förväntade resultat</u>:

Nytt [!UICONTROL shipment], [!UICONTROL invoice] och [!UICONTROL credit memo] visas.

<u>Faktiska resultat</u>:

Nytt [!UICONTROL shipment], [!UICONTROL invoice]och [!UICONTROL credit memo] visas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
