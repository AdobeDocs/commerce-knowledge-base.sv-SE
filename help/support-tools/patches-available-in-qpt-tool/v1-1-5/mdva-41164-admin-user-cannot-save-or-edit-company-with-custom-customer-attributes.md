---
title: 'MDVA-41164: Det går inte att spara eller redigera företag med anpassade kundattribut'
description: MDVA-41164-korrigeringen löser problemet där administratörsanvändaren inte kan spara eller redigera ett företag med anpassade kundattribut för filer eller bilder av någon typ. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 är installerat. Korrigerings-ID är MDVA-41164. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 24338895-68b4-404c-bedd-46cfc7e983a0
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-41164: Det går inte att spara eller redigera företag med anpassade kundattribut

MDVA-41164-korrigeringen löser problemet där administratörsanvändaren inte kan spara eller redigera ett företag med anpassade kundattribut för filer eller bilder av någon typ. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 har installerats. Korrigerings-ID är MDVA-41164. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren kan inte spara eller redigera ett företag med anpassade kundattribut för filer eller bilder av någon typ.

<u>Förutsättningar</u>:

B2B-modulen är installerad.

<u>Steg som ska återskapas</u>:

1. Aktivera företag i **Lagrar** > **Konfig** > **B2B-funktioner**.
1. Skapa ett kundattribut i **Lagrar** > **Attribut** > **Kunder** > **Lägg till nytt attribut**:
   * Indatatyp: Fil (bifogad)
   * Visa på Storefront: Ja
   * Sorteringsordning: Alla
   * Forms att använda i: Markera alla
1. Skapa ett nytt företag i **Kunder** > **Företag** > **Lägg till nytt företag** och överför en fil för det nya attributet som skapas ovan.

<u>Förväntade resultat</u>:

Användaren kan slutföra skapandet av företaget och bilagan överförs utan fel.

<u>Faktiska resultat</u>:

* Du får ett felmeddelande: *Något gick fel när filen sparades.*
* Undantagsloggen innehåller en post som följande:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
