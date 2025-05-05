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

Korrigeringen ACSD-47803 åtgärdar ett problem där ej lagrade konfigurerbara produktfärgrutor visas som tillgängliga. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 har installerats. Korrigerings-ID är ACSD-47803. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Färgrutor som inte kan konfigureras visas som tillgängliga.

<u>Steg som ska återskapas</u>:

>[!NOTE]
>
>Stegen nedan visar exempeldata som exempel.

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** i [!UICONTROL Commerce] Admin och ställ in **[!UICONTROL Display Out of Stock Products]** på *Ja*.
1. Gå återigen från Admin till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** och redigera en konfigurerbar produkt på produktredigeringssidan (till exempel &quot;WB04&quot; SKU, om du använder exempeldata):
   * För en av konfigurationsvarianterna anger du kvantiteten till *0* (till exempel för &quot;WB04-M-Purple&quot;).
1. Öppna den konfigurerbara produkten i butiken.
1. Välj produktstorlek för den konfigurerbara varianten med noll lager (d.v.s. &quot;M&quot;).

<u>Förväntade resultat</u>:

Alternativen som ligger utanför lagret är inaktiverade och markerade som [!UICONTROL Out of Stock].

<u>Faktiska resultat</u>:

Alla färgrutor är aktiverade, även den som är [!UICONTROL Out of Stock].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
