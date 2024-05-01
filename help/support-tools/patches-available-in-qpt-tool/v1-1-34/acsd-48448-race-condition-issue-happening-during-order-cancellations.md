---
title: 'ACSD-48448: Problem med spårningsvillkor under orderannulleringar som orsakar dubblerad inmatning i registret lager_reservation'
description: Använd patchen ACSD-48448 för att åtgärda Adobe Commerce-prestandaproblemet där problemet med ansiktsvillkor inträffar under orderannulleringarna, vilket orsakar dubblerade poster i tabellen Inventering_reservation.
feature: Orders, Checkout
role: Admin
exl-id: 69d00219-bc9f-4531-9e85-38476c2258ed
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-48448 *[!UICONTROL Race]* villkorsproblem vid orderannulleringar som orsakar dubblettinmatning i `inventory_reservation` table

Korrigeringen ACSD-48448 åtgärdar ett problem där *[!UICONTROL Race]* problem inträffar vid orderannulleringar, vilket orsakar dubblettposter i `inventory_reservation` tabell. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.34 är installerat. Korrigerings-ID är ACSD-48448. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2 och 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

*[!UICONTROL Race]* problem inträffar vid orderannulleringar, vilket orsakar dubblettposter i `inventory_reservation` tabell.

<u>Steg som ska återskapas</u>:

1. Beställ.
1. Kontrollera `inventory_reservation` tabell för att se till att det finns en post för `order_placed` -händelse.
1. Kör det bifogade skriptet för att avbryta ordningen parallellt (kom ihåg att ändra URL:en och orderID).

`bash cancel_order.sh`

```
#!/bin/bash
baseUrl=" "
orderId=3
token=$(curl --location --request POST "${baseUrl}rest/V1/integration/admin/token" \
 -H 'Content-Type: application/json' \
 -d '{
  "username": "admin",
  "password": "password"
}')
echo ${token//\"/}
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
 &
sleep 0.1;
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
wait
```

<u>Förväntade resultat</u>:

Posterna dupliceras inte.

<u>Faktiska resultat</u>:

Dubblettposter skapas i `inventory_reservation` tabell för `order_canceled`.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
