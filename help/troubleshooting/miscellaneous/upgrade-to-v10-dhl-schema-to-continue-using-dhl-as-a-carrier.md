---
title: Uppgradera till v10 DHL-schema för att fortsätta erbjuda DHL-leverans
description: Den här artikeln innehåller en lösning som tillåter handlare att fortsätta erbjuda DHL-leverans efter att DHL-schema 6.2 har tagits bort i december 2022, genom att uppgradera till schema 10.0 eller genom att tillämpa AC-3023-korrigeringen.
exl-id: eed83713-2d6a-4360-bfa1-bebd4d604f2f
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Uppgradera till DHL-schema version 10.0 för att fortsätta erbjuda DHL-leverans

Den här artikeln innehåller en lösning som tillåter handlare att fortsätta erbjuda DHL-leverans efter att DHL-schemaversionen version 6.2 har tagits bort i slutet av december 2022.

## Berörda produkter och versioner

* Adobe Commerce 2.4.5 och tidigare versioner, alla distributionsmetoder.

## Problem

I augusti 2022 släppte vi [uppgraderingen av DHL-schemaversion 6.2. tillsammans med en korrigeringsfil](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) så att handlarna kan fortsätta erbjuda DHL-leverans. DHL introducerar återigen ett nyare schema - version 10.0 - i oktober 2022, och den tidigare versionen (6.2-schema) kommer att bli inaktuell i slutet av december 2022. Adobe Commerce 2.4.5 och tidigare DHL-integrering stöder endast version 6.2.

## Lösning

Adobe Commerce 2.4.5-p1 och 2.4.4-p2, släppt i oktober 2022, innehåller den nya DHL-schemaversionen 10.0. Handlare som uppgraderar till 2.4.5-p1 och 2.4.4-p2 behöver alltså inte göra något för att fortsätta erbjuda DHL-leveranser. Vi uppmuntrar alla handlare att uppgradera till 2.4.5-p1 och 2.4.4-p2 innan DHL-schema 6.2 ersätts i slutet av december 2022.

Handlare som inte vill uppgradera till 2.4.5-p1 och 2.4.4-p2 måste installera en patch om de vill fortsätta erbjuda DHL-leverans efter december 2022.

## Lappa

Korrigerings-ID:t är AC-3023 och det är tillgängligt i [!DNL Quality Patches Tool] version 1.1.21.

Använd följande länkar om hur du använder [!DNL Quality Patches Tool] och installera korrigeringsfiler beroende på distributionsmetoder:

* Adobe Commerce lokalt och Magento Open Source: [Kvalitetskorrigeringsverktyg > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i Adobe Experience League.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

**Korrigeringen gäller för följande Adobe Commerce-versioner (alla distributionsmetoder):**

* 2.3.7, 2.4.0, 2.4.1, 2.4.2, 2.4.3, 2.4.3-p2, 2.4.3-p3, 2.4.4

## Användbara länkar

* [[!DNL Quality Patches Tool] > Versionsinformation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) i Adobe Experience League.

* [[!DNL Quality Patches Tool]: Sök efter patchar ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i Adobe Experience League.

## Relaterad läsning

* [Använd en patch för att fortsätta erbjuda DHL som fraktfirma](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) i vår kunskapsbas för support.

* [Fraktfirmor > DHL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl.html) i användarhandboken.
* [Konfigurationsreferens > Försäljning > Leveransmetoder](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/delivery-methods.html) i användarhandboken.
