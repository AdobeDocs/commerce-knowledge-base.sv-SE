---
title: 'ACSD-47803: Konfigurerbara färgrutor som inte finns installerade och visas som tillgängliga'
description: Använd patchen ACSD-47803 för att åtgärda Adobe Commerce-problemet där färdiga konfigurerbara färgrutor visas som tillgängliga.
exl-id: 28b3f378-a790-4af6-9627-5bd8571523fd
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-47803: Konfigurerbara färgrutor som inte finns installerade visas som tillgängliga

Korrigeringen ACSD-47803 åtgärdar ett problem där ej lagrade konfigurerbara produktfärgrutor visas som tillgängliga. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 är installerat. Korrigerings-ID är ACSD-47803. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Färgrutor som inte kan konfigureras visas som tillgängliga.

<u>Steg som ska återskapas</u>:

>[!NOTE]
>
>Stegen nedan visar exempeldata som exempel.

1. I [!UICONTROL Commerce] Admin, gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** och ange **[!UICONTROL Display Out of Stock Products]** till *Ja*.
1. I Admin navigerar du återigen till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** och redigera en konfigurerbar produkt på produktredigeringssidan (t.ex. &quot;WB04&quot; SKU, om du använder exempeldata):
   * För en av konfigurationsvarianterna anger du kvantiteten till *0* (till exempel för&quot;WB04-M-Purple&quot;).
1. Öppna den konfigurerbara produkten i butiken.
1. Välj produktstorlek för den konfigurerbara varianten med noll lager (d.v.s. &quot;M&quot;).

<u>Förväntade resultat</u>:

Alternativen som inte finns i lager är inaktiverade och markerade som [!UICONTROL Out of Stock].

<u>Faktiska resultat</u>:

Alla färgrutor aktiveras, även den som [!UICONTROL Out of Stock].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
