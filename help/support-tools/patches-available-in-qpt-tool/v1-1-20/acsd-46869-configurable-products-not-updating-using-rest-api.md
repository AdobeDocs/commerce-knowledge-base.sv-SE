---
title: 'ACSD-46869: Konfigurerbara produkter som inte uppdateras med REST API vid utcheckning'
description: Korrigeringen ACSD-46869 åtgärdar ett problem där konfigurerbara produkter inte uppdateras med REST API vid utcheckningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 är installerat. Korrigerings-ID är ACSD-46869. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869: Konfigurerbara produkter som inte uppdateras med REST API vid utcheckning

Korrigeringen ACSD-46869 åtgärdar ett problem där konfigurerbara produkter inte uppdateras med REST API vid utcheckning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 har installerats. Korrigerings-ID är ACSD-46869. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du paketet `magento/quality-patches` till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL QPT] landningssidan](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Konfigurerbara produkter uppdateras inte med REST API under utcheckningen.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med färg- och storleksattribut.
1. Välj **[!UICONTROL Options]** och lägg till produkten i kundvagnen.
1. Gå till **[!UICONTROL Checkout]**, uppdatera storleken flera gånger förutom för kvantitet, och kontrollera begäran och svar.
1. Du får följande svar när du uppdaterar storleken.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Förväntade resultat</u>:

Värdet uppdateras enligt ändringarna.

<u>Faktiska resultat</u>:

`option_value` uppdateras inte, så när ordningen placeras har den det gamla storleksvärdet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tools] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden för kvalitetspatchar.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för ditt Adobe Commerce-problem med hjälp av [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i [!DNL QPT] finns i [Patchar som är tillgängliga i  [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i guiden för verktyget för kvalitetskorrigeringar.
