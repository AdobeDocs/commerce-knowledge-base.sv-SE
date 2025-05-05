---
title: 'MDVA-39713: Användaren kan redigera starttiden för aktiv schemalagd uppdatering'
description: MDVA-39713-korrigeringen åtgärdar ett problem där en användare kan redigera starttiden för en aktiv schemalagd uppdatering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-39713. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: c7221fdb-5fc0-4179-8d4c-c9e1f0d00692
feature: CMS
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-39713: Användaren kan redigera starttiden för aktiv schemalagd uppdatering

MDVA-39713-korrigeringen åtgärdar ett problem där en användare kan redigera starttiden för en aktiv schemalagd uppdatering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-39713. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.3.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren kan redigera starttiden för en aktiv schemalagd uppdatering.

<u>Steg som ska återskapas</u>:

1. Skapa nya CMS-sidor.
1. Välj **Schemalägg ny uppdatering** och ställ in **Startdatum** på aktuell +1 minut.
1. Aktivera den schemalagda uppdateringen genom att köra kommandot `bin/magento cron:run --group=staging` i den lokala miljön. Vänta i några minuter och kontrollera om schemat är aktivt.
1. Uppdatera sidan när schemat är aktivt.
1. Klicka på **Visa/redigera** i avsnittet Schemalagda ändringar.
1. Redigera tiden genom att lägga till +2 minuter och spara ändringen.
1. Spara CMS.
1. Kör följande kommando igen: `bin/magento cron:run --group=staging`.
1. Klicka på **Visa/redigera** för den schemalagda uppdateringen.

<u>Förväntade resultat</u>:

Användaren kan inte redigera starttiden för en aktiv schemalagd uppdatering.

<u>Faktiska resultat</u>:

Användaren får ett fel som *Item (Magento\Cms\Model\Page) med samma ID &quot;11&quot; finns redan.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
