---
title: 'MDVA-30972: orderstatus felaktig leverans skapad via REST API'
description: MDVA-30972-korrigeringen löser problemet där orderstatusen ändras felaktigt när leveransen skapas via REST API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat.
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972: orderstatus felaktig leverans skapad via REST API

MDVA-30972-korrigeringen löser problemet där orderstatusen ändras felaktigt när leveransen skapas via REST API. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 till 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När en delleverans skapas från administratören via REST API för en beställning med *Misstänkt bedrägeri* orderstatus, orderstatus ändras till *Bearbetar*. Det borde stanna på *Misstänkt bedrägeri*.

<u>Förutsättningar</u>:

* PayPal EC eller någon annan onlinebetalningsmetod har konfigurerats.
* Integrering för REST API har konfigurerats.

<u>Steg som ska återskapas</u>:

1. Skapa en order med två eller flera objekt.
1. Logga in på **Administratör** > **Försäljning** > **Beställningar**. Öppna den order du nyss skapade.
1. Bläddra nedåt till på sidan med orderinformation **Ordersumma**. Klicka på **Status** nedrullningsbar meny och välj *Misstänkt bedrägeri*. Klicka sedan på **Skicka kommentar** -knappen.
1. Kontrollera att ordern har *Misstänkt bedrägeri* status nu.
1. Skapa en leverans för en artikel från ordern med REST API:

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. Öppna ordern i Admin igen och kontrollera dess status.

<u>Förväntade resultat</u>:

* Orderstatus = *Misstänkt bedrägeri*.
* Orderstatus ändras inte om samma leverans skapas från Admin.

<u>Faktiska resultat</u>:

Orderstatus = *Bearbetar*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
