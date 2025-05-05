---
title: 'ACSD-48417: SQL-fel efter att en schemaändring har skapats'
description: Använd patchen ACSD-48417 för att åtgärda Adobe Commerce-problemet där ett SQL-fel uppstår när du har skapat en schemaändring för en produkt och sparat en annan produkt.
exl-id: 2bbf3bb5-dec8-43b3-81f1-be0dc53d1f46
feature: Storage
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-48417: SQL-fel efter att en schemaändring har skapats

Korrigeringen ACSD-48417 åtgärdar ett problem där ett SQL-fel uppstår efter att en schemaändring för en produkt har skapats och en annan produkt har sparats. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 har installerats. Korrigerings-ID är ACSD-48417. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett SQL-fel visas när du har skapat en schemaändring för en produkt och sparat en annan produkt.

<u>Steg som ska återskapas</u>:

1. Installera Magento 2.4-develop EE + Sample Data.
1. Gå till administratörspanelen > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Redigera valfri produkt (t.ex. Joust Duffle Bag [SKU: 24 MB01]).
1. Schemalägg en ny uppdatering:
   * Välj **[!UICONTROL Save as a New Update]**
   * Uppdateringsnamn: &quot;Uppdatering 1&quot;
   * Startdatum: aktuell tid +1 min
   * Slutdatum: aktuell tid +1 timme
   * Ändra produktnamnet till: &quot;Joust Duffle Bag 2&quot;
   * Spara produkten.
1. Gå till CLI och kör cron och vänta tills schemat har tillämpats.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. Återigen, gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** och redigera alla konfigurerbara produkter (t.ex. Chaz Kangeroo Hoodie [SKU: MH01 ]).

   * Inaktivera alla varianter. Gå till kolumnen Åtgärder > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**.
   * Spara den konfigurerbara versionen.

<u>Förväntade resultat</u>:

Inget fel uppstod när produkten sparades.

<u>Faktiska resultat</u>:

Följande fel inträffar:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
