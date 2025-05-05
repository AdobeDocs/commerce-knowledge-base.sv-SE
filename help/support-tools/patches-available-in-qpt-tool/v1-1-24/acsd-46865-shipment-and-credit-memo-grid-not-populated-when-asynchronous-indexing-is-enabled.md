---
title: 'ACSD-46865: [!UICONTROL shipment] och [!UICONTROL credit memo] har inte fyllts i när [!UICONTROL asynchronous indexing] är aktiverat'
description: Använd korrigeringen ACSD-46865 för att åtgärda Adobe Commerce-problemet där [!UICONTROL shipment] och [!UICONTROL credit memo] rutnät inte fylls i när [!UICONTROL asynchronous indexing] är aktiverat.
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] och [!UICONTROL credit memo] fylldes inte i när [!UICONTROL asynchronous indexing] är aktiverat

Korrigeringen ACSD-46865 åtgärdar ett problem där [!UICONTROL shipment] och [!UICONTROL credit memo] rutnät inte fylls i när [!UICONTROL asynchronous indexing] aktiveras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 har installerats. Korrigerings-ID är ACSD-46865. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL Shipment] och [!UICONTROL credit memo] rutnät fylls inte i när [!UICONTROL asynchronous indexing] är aktiverat.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *JA* i [!DNL Commerce] Admin.
2. Gå igen till **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Rensa konfigurationscachen.
4. Gör en ny gästbeställning av en enkel produkt.
5. Spring cron.
6. Öppna ordern i [!UICONTROL Commerce]-administratören genom att gå till **[!UICONTROL Sales]** > **[!UICONTROL Orders]** och generera en faktura och en kreditnota.
7. Flytta ordningen till [!UICONTROL Archive].
8. Skapa en ny order för en enkel produkt.
9. Spring cron.
10. Gå till den nya ordern och generera en ny leverans, en faktura och en kreditnota.
11. Spring cron.
12. Kontrollera rutnäten [!UICONTROL shipments], [!UICONTROL invoices] och [!UICONTROL credit memo] i administratören.

<u>Förväntade resultat</u>:

Nya [!UICONTROL shipment], [!UICONTROL invoice] och [!UICONTROL credit memo] visas.

<u>Faktiska resultat</u>:

Nya [!UICONTROL shipment], [!UICONTROL invoice] och [!UICONTROL credit memo] visas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
