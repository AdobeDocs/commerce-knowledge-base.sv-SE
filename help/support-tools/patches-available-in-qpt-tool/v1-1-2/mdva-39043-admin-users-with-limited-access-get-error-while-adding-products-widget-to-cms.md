---
title: 'MDVA-39043: Administratörsanvändare får felmeddelande när widgeten läggs till på CMS-sidan'
description: Korrigeringen MDVA-39043 åtgärdar ett problem där administratörsanvändare med begränsad åtkomst får ett fel när de lägger till widgeten"Produkter" på CMS-sidan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 är installerat. Korrigerings-ID är MDVA-39043. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 63057351-e972-4575-9bf0-e818f590b40a
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-39043: Administratörsanvändare får ett fel när widgeten läggs till på CMS-sidan

Korrigeringen MDVA-39043 åtgärdar ett problem där administratörsanvändare med begränsad åtkomst får ett fel när de lägger till widgeten&quot;Produkter&quot; på CMS-sidan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 har installerats. Korrigerings-ID är MDVA-39043. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändare med begränsad åtkomst får ett fel när widgeten&quot;Produkter&quot; läggs till på CMS-sidan.

<u>Steg som ska återskapas</u>:

1. Logga in på backend med administratören som endast har åtkomst till redigeringsinnehåll.
1. Gå till **Innehåll** > **Sidor**.
1. Öppna en sida som du vill redigera.
1. Redigera innehållet med **Page Builder**.
1. Lägg till widgeten **Produkt** från avsnittet **Lägg till innehåll**.
1. Klicka på **Konfigurera** i widgeten **Produkt**.

<u>Förväntade resultat</u>:

Inget fel visas.

<u>Faktiska resultat</u>:

Följande felmeddelande har tagits emot:

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
