---
title: 'ACSD-46869: Konfigurerbara produkter som inte uppdateras med REST API vid utcheckning'
description: Korrigeringen ACSD-46869 åtgärdar ett problem där konfigurerbara produkter inte uppdateras med REST API vid utcheckningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 är installerat. Korrigerings-ID är ACSD-46869. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869: Konfigurerbara produkter som inte uppdateras med REST API vid utcheckning

Korrigeringen ACSD-46869 åtgärdar ett problem där konfigurerbara produkter inte uppdateras med REST API vid utcheckning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 är installerat. Korrigerings-ID är ACSD-46869. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL QPT] landningssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Konfigurerbara produkter uppdateras inte med REST API under utcheckningen.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med färg- och storleksattribut.
1. Välj **[!UICONTROL Options]** och lägg produkten i kundvagnen.
1. Gå till **[!UICONTROL Checkout]**, uppdaterar storleken flera gånger förutom för kvantitet och kontrollerar förfrågan och svar.
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

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tools] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden för verktyget Kvalitetspatchar.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) i vår kunskapsbas för support.

Mer information om andra patchar finns i [!DNL QPT], se [Patchar finns i [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i guiden för verktyget Kvalitetspatchar.
