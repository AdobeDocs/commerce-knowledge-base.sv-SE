---
title: 'MDVA-41046: Enkla produkter med anpassade alternativ som inte är tillgängliga för tilldelning'
description: MDVA-41046-korrigeringen löser problemet där enkla produkter med anpassade alternativ inte är tillgängliga för tilldelning till konfigurerbara/grupperade produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 är installerat. Korrigerings-ID är MDVA-41046. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 01229a69-c72a-4189-9be5-1761073b74ee
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-41046: Enkla produkter med anpassade alternativ som inte är tillgängliga för tilldelning

MDVA-41046-korrigeringen löser problemet där enkla produkter med anpassade alternativ inte är tillgängliga för tilldelning till konfigurerbara/grupperade produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 har installerats. Korrigerings-ID är MDVA-41046. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Enkla produkter med anpassade alternativ är inte tillgängliga för tilldelning till konfigurerbara/grupperade produkter.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt med anpassningsbara alternativ och ange ett värde för det konfigurerbara attributet.
   * Använd *Color* som konfigurerbart attribut och välj *Gul* som färgvärde.
1. Spara den enkla produkten.
1. Gå nu till sidan Skapa konfigurerbar produkt.
1. Gå igenom guiden Skapa konfiguration och se till att välja *Gul* som attributfärg.
1. Om du inte vill spara den konfigurerbara produkten väljer du&quot;Välj en annan produkt&quot; i listrutan Välj.
1. Då öppnas ett produktrutnät som filtreras med färgattributet gul. Välj nu den enkla produkt som du skapat tidigare med anpassningsbara alternativ.
1. Spara den konfigurerbara produkten.

<u>Förväntade resultat</u>:

Den enkla produkten med anpassade alternativ är tillgänglig för tilldelning (visas i rutnät) i steg 6.

<u>Faktiska resultat</u>:

Konfigurationsavsnittet är tomt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
