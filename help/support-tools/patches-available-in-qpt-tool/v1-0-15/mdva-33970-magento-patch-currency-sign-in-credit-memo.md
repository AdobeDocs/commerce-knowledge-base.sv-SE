---
title: 'MDVA-33970-korrigering: valutasymbol i kreditnota'
description: MDVA-33970-korrigeringen löser problemet där ett dollartecken ($) visades i stället för den lokaliserade valutan i en kreditnota. Detta inträffar när ett **Website**-omfång används för ett **Price**-attribut.
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# MDVA-33970-korrigering: valutasymbol i kreditnota

MDVA-33970-korrigeringen löser problemet där ett dollartecken ($) visades i stället för den lokaliserade valutan i en kreditnota. Detta inträffar när en **webbplats**-omfattning används för ett **Price** -attribut.

Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 är installerat. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.3.4-p2

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce i molninfrastruktur och Adobe Commerce lokalt 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förhandsvillkor</u>:

I det här exemplet används följande inställningar:

* Det finns två webbplatser - var och en har en **Store** och en **Store**.
* **Standardkonfigurationen** har Singapore-dollar som **Valuta** (**Lager > Konfiguration > Allmänt > Valutainställningar**):
   * **Basvaluta** = *Singapore-dollar*
   * **Standardvisningsvaluta** = *Singapore-dollar*
   * **Tillåtna valutor** = *Singapore-dollar*
* **Webbplats 1** har en **standardkonfiguration**.
* **På webbplatsen 2** finns malaysisk ringgit som **Valuta**:
   * **Basvaluta** = *malaysisk ringgit*
   * **Standardvisningsvaluta** = *malaysisk ringgit*
   * **Tillåtna valutor** = *Malaysian Ringgit*
* Gå till **Lager > Valutasymboler** och ange:
   * **MYR (malaysisk ringgit)** = *RM*
   * **SGD (Singapore-dollar)** = *SGD* (**Använd standard** = *Markerad*)
* En del **produkt** finns.

<u>Steg som ska återskapas</u>:

1. Gör en **beställning** från **webbplatsen** (du kan konfigurera den som Standard för att undvika ytterligare inställningar).
1. Logga in på **Admin**.
1. Öppna den nyligen skapade ordern.
1. Kontrollera att **valutasymbolen** = *RM*.
1. Skapa en **faktura**.
1. Kontrollera att **valutasymbolen** = *RM* finns på fakturan.
1. Skapa en **kreditnota**.
1. Kontrollera att **valutasymbolen** ** ** = *RM* i **kreditnotan**.
1. Öppna fliken **Kreditnotor** i **Beställning**.
1. Kontrollera **valutasymbolen** i rutnätet.
1. Öppna **Försäljning > Kreditnotor**.
1. Kontrollera **valutasymbolen** i rutnätet.

<u>Förväntade resultat</u>:

Den korrekta lokaliserade valutasymbolen används som förväntat.

<u>Faktiska resultat</u>:

Dollar-tecknet ($) används, även om det inte har konfigurerats i administratörsinställningarna.

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
