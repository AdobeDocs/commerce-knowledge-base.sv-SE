---
title: 'MDVA-42046: Felaktigt värde tilldelat för produktattribut'
description: MDVA-42046-korrigeringen åtgärdar ett problem där ett felaktigt värde tilldelas för produktattributet när en produkt som har ett datuminmatningsfält uppdateras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-42046. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 837f5582-849c-43a3-ae02-87f71fb96061
feature: Attributes, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-42046: Felaktigt värde tilldelat för produktattribut

MDVA-42046-korrigeringen åtgärdar ett problem där ett felaktigt värde tilldelas för produktattributet när en produkt som har ett datuminmatningsfält uppdateras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-42046. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.3.5-p2 och 2.4.0 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du har sparat en produkt med `news_from_date`- och/eller `news_to_date`-fält återställs värdena från dessa fält till standardvärdena.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Exportera den produkt som skapades i steg ett.
1. I den exporterade CSV-filen anger du värden i fälten `news_from_date` och `news_to_date`. Exempel: 2021-05-15 och 2021-06-18.
1. Importera produkten med den ändrade CSV-filen.
1. Lägg till ytterligare kolumner&quot;Ange produkten som ny från datum&quot; och&quot;Ange produkten som ny till datum&quot; i produktrutnätet.
1. Öppna redigeringssidan för produkten och klicka utan ändringar på **Spara**.
1. Gå tillbaka till produktrutnätet och kontrollera produktinformationen.

<u>Förväntade resultat</u>:

Både&quot;Ange produkten som ny från datum&quot; och&quot;Ange produkten som ny till datum&quot; är desamma som innan du sparar.

<u>Faktiska resultat</u>:

* Värdena i kolumnerna&quot;Ange produkten som ny från datum&quot; och&quot;Ange produkten som ny till datum&quot; har ändrats.

* Kolumnen Ange produkten som ny från datum visar det aktuella datumet och kolumnen Ange produkten som ny till datum är tom.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
