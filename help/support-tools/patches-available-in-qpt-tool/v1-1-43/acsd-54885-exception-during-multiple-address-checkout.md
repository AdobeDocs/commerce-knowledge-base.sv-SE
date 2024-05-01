---
title: 'ACSD-54885: Undantag under utcheckning av flera adresser när administratören loggar in som kund'
description: Använd korrigeringsfilen ACSD-54885 för att åtgärda Adobe Commerce-problemet när ett fel inträffar vid utcheckning av flera adresser när administratören använder *[!UICONTROL Login as Customer]* funktionalitet.
feature: Checkout
role: Admin, Developer
exl-id: 524ec96b-1465-4673-9fbe-1a9c086b7e87
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54885: Undantag vid utcheckning av flera adresser när administratören loggar in som kund

Korrigeringen ACSD-54885 åtgärdar ett problem där ett fel inträffar vid utcheckning av flera adresser när administratören använder *[!UICONTROL Login as Customer]* funktionalitet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 är installerat. Korrigerings-ID är ACSD-54885. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel inträffar vid utcheckning av flera adresser när administratören använder *[!UICONTROL Login as Customer]* funktionalitet.

<u>Steg som ska återskapas</u>:

1. Se till att *[!UICONTROL Login as Customer]* är aktiverat. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Skapa en enkel produkt.
1. Skapa ett nytt kundkonto med en adress.
1. Gå till kundkontot i serverdelen:

   * Gå till **[!UICONTROL Account Information]** och ange *[!UICONTROL Allow remote shopping assistance]* = *Ja*.
   * Klicka på **[!UICONTROL Login as Customer]**.

1. Lägg produkten i kundvagnen och fortsätt till *[!UICONTROL Checkout with multiple addresses]*.
1. Uppdatera produktkvantiteten.
1. Försök gå tillbaka till kundvagnen.

<u>Förväntade resultat</u>:

Du kan uppdatera kundvagnen och använda flera adressköp.

<u>Faktiska resultat</u>:

Du får följande fel när du går tillbaka till kundvagnen.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
