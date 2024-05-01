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

MDVA-33970-korrigeringen löser problemet där ett dollartecken ($) visades i stället för den lokaliserade valutan i en kreditnota. Detta inträffar när en **Webbplats** omfånget används för **Pris** -attribut.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 är installerat. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce om molninfrastruktur 2.3.4-p2

**Kompatibel med Adobe Commerce:** Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förhandsvillkor</u>:

I det här exemplet används följande inställningar:

* Det finns två webbplatser - var och en har en **Butik** och **Butiksvy**.
* The **Standardkonfiguration** har Singapore-dollar som **Valuta** (**Stores > Configuration > General > Currency Setup**):
   * **Basvaluta** = *Singaporedollar*
   * **Standardvisningsvaluta** = *Singaporedollar*
   * **Tillåtna valutor** = *Singaporedollar*
* **Webbplats 1** har en **Standardkonfiguration**.
* **Webbplats 2** har malaysiska ringgit som **Valuta**:
   * **Basvaluta** = *Malaysiska ringgit*
   * **Standardvisningsvaluta** = *Malaysiska ringgit*
   * **Tillåtna valutor** = *Malaysiska ringgit*
* Gå till **Lager > Valutasymboler** och Ange:
   * **MYR (malaysiska ringgit)** = *RM*
   * **SGD (Singapore-dollar)** = *SGD* (**Använd standard** = *Markerad*)
* Några **Produkt** finns.

<u>Steg som ska återskapas</u>:

1. Gör en **Beställning** från **Webbplats 2** (du kan konfigurera det som standard för att undvika ytterligare inställningar).
1. Logga in på **Administratör**.
1. Öppna den nyligen skapade ordern.
1. Kontrollera att **Valutasymbol** = *RM*.
1. Skapa en **Faktura**.
1. Kontrollera att **Valutasymbol** = *RM* i fakturan.
1. Skapa en **Kreditnota**.
1. Kontrollera att **Valutasymbol**  ** ** = *RM* i **Kreditnota**.
1. Öppna **Kreditnotor** tabba in **Beställning**.
1. Kontrollera **Valutasymbol** i rutnätet.
1. Öppna **Försäljning > Kreditnotor**.
1. Kontrollera **Valutasymbol** i rutnätet.

<u>Förväntade resultat</u>:

Den korrekta lokaliserade valutasymbolen används som förväntat.

<u>Faktiska resultat</u>:

Dollar-tecknet ($) används, även om det inte har konfigurerats i administratörsinställningarna.

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
