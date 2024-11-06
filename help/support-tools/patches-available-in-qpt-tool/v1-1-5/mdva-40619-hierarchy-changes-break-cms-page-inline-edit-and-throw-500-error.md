---
title: 'MDVA-40619: Hierarkiändringar bryter CMS sidredigering och orsakar 500-fel'
description: Korrigeringen MDVA-40619 löser problemet där CMS sidhierarki bryter CMS sidinfogade redigering och ger"500-fel". Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 är installerat. Korrigerings-ID är MDVA-40619. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: c003d845-1ba0-49c0-9f1a-a4b0ec00f30c
feature: CMS
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40619: Ändringar i hierarkin bryter CMS sidredigering och orsakar 500-fel

Korrigeringen MDVA-40619 löser problemet där CMS sidhierarki bryter CMS sidinfogade redigering och ger&quot;500-fel&quot;. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 har installerats. Korrigerings-ID är MDVA-40619. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ändringar i CMS sidhierarki bryter CMS sidinline-redigering och orsakar&quot;500-fel&quot;.

<u>Steg som ska återskapas</u>:

1. Gå till panelen Admin > **Innehåll** > **Hierarki**.
1. Välj Standardbutiksvy.
1. Avmarkera Använd hierarkin för den överordnade noden.
1. Markera sidan manuellt och klicka på **Spara**.
1. Gå sedan till **Innehåll** > **Sidor**.
1. Försök redigera en CMS-sida från stödrastret.
1. Klicka på **Spara**.

<u>Förväntade resultat</u>:

Sidan har sparats.

<u>Faktiska resultat</u>:

Du får följande fel:

*Ett tekniskt problem med servern skapade ett fel. Försök igen för att fortsätta med det du gjorde. Försök igen senare om problemet kvarstår.*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
