---
title: 'MDVA-33168: API async-slutpunkten tar bort specialpris'
description: Korrigeringen MDVA-33168 åtgärdar ett problem där API:ts asynkrona slutpunkt för uppdatering av ett produktattribut tar bort ett specialpris.
exl-id: 4dd26215-b140-4924-8f4d-0d062e5fda2d
feature: REST, Orders, Personalization
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-33168: API async-slutpunkten tar bort specialpriset

Korrigeringen MDVA-33168 åtgärdar ett problem där API:ts asynkrona slutpunkt för uppdatering av ett produktattribut tar bort ett specialpris.

Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Patch-ID:t är MDVA-33168. Observera att problemet är planerat att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.3-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.3 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Skapa två webbplatser med butiker.
1. Gå till **Lager > Konfigurationer > Katalog > Katalog > Pris > Katalog** och ange **prisomfång** = *Webbplats*.
1. Skapa ett *texttyp*-produktattribut. Låt alla alternativ vara som standard.
1. Lägg till det attribut som skapas i standardattributuppsättningen.
1. Skapa en enkel produkt att använda med en paketprodukt.
1. Skapa en paketprodukt med följande exempelalternativ:
   * **Aktivera produkt** = *Ja*.
   * **Attributuppsättning** = *Standard*.
   * **Produktnamn** = *bundle-1*.
   * **SKU** = *bundle-1*.
   * **Dynamisk SKU** = *Ja*.
   * **Pris** = *$100.00*.
   * **Skatteklass** = *Skattepliktiga varor*.
   * **Stock-status** = *I Stock*.
1. Ange följande exempelalternativ under **Paketobjekt**:
   * **Leveranspaket** = *Tillsammans*.
   * **Alternativtitel** = *test*, **Indatatyp** = *Alternativknappar*, kryssrutan **Obligatorisk** = *checked*.
   * **Är standard**, kryssruta = *avmarkerad*.
   * **Namn** = *enkel-100*.
   * **SKU** = *simple-100*.
   * **Pris** = *100.00*.
   * **Pristyp** = *Fast*.
   * **Standardantal** = *1*.
   * **Användardefinierad** kryssruta = *avmarkerad*.
1. Växla omfånget till en annan butik än standardbutiken och ange specialpriset. (Exempel: på sidan **Avancerade priser** anger du **Specialpris** = *4%* och **Prisvy** = *Prisintervall*.)
1. Uppdatera bara det nya attributet i lagringsområdet som inte är standard, som i följande exempel:

   ```php
       PUT {{base_url}}/rest/en_au/async/V1/products/{{sku}}    {        "product": {            "custom_attributes": [                {                    "attribute_code": "text_attr",                    "value": 21                                   }            ]                    }    }
   ```

<u>Förväntade resultat</u>:

Andra attributvärden är desamma när du uppdaterar ett produktattribut med asynkron rest-API, som förväntat.

<u>Faktiska resultat</u>:

Specialpriset, som angavs med hjälp av asynkront rest-API under butiksomfånget, tas bort.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [korrigeringsfilerna i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
