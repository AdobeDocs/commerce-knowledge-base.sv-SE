---
title: 'ACSD-57003: Orderstatus ändras till *Fullständigt* i stället för att ändras till *Bearbetning*'
description: Använd patchen ACSD-57003 för att åtgärda Adobe Commerce-problemet där orderstatusen ändras till *Complete* i stället för att ändras till *Processing*.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: c3c59185-c447-46fa-b404-6c4a4a300315
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-57003: Orderstatus ändras till *Complete* i stället för att byta till *Bearbetar*

Korrigeringen ACSD-57003 åtgärdar ett problem där orderstatusen ändras till *Complete* i stället för att byta till *Bearbetar*. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.46 är installerat. Korrigerings-ID är ACSD-57003. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Orderstatusen ändras till *Complete* i stället för att byta till *Bearbetar* när en order delvis återbetalas och delvis skickas.

<u>Steg som ska återskapas</u>:

1. Skapa en beställning med två konfigurerbara produkter.
1. Fakturera alla artiklar.
1. Leverera bara den första artikeln.
1. Återbetala/skapa en kreditnota för endast den levererade artikeln (*första objektet*).
1. Kontrollera orderstatus.

<u>Förväntade resultat</u>:

Orderstatus ska finnas i _Bearbetar_ tillstånd.

<u>Faktiska resultat</u>:

Orderstatus ändras till *Complete* efter att en kreditnota har skapats för den delvis levererade artikeln.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
