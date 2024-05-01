---
title: 'ACSD-49389: Redo för att hämta e-post som skickas av API när den inte är klar för hämtning'
description: Använd patchen ACSD-49389 för att åtgärda Adobe Commerce-problemet där ett e-postmeddelande som är klart för hämtning skickas av API:t när beställningen inte är klar för hämtning.
exl-id: a1baae06-cf36-448b-bda4-aff1e5ca68db
feature: REST, Communications
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49389: Redo för hämtning av e-post som skickas av API när den inte är klar för hämtning

Korrigeringen ACSD-49389 åtgärdar ett problem där ett e-postmeddelande som är klart för hämtning skickas av API:t när beställningen inte är klar för hämtning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 är installerat. Korrigerings-ID är ACSD-49389. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [QPT-landningssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett e-postmeddelande som är klart för hämtning skickas av API:t när beställningen inte är klar för hämtning.

<u>Steg som ska återskapas</u>:

1. Aktivera *[!UICONTROL In-Store Delivery]* -metod.
1. Skapa en Stock-källa med hämtningsplats aktiverad.
1. Skapa ett nytt arkiv med huvudwebbplatsen med källan som skapas ovan.
1. Skapa en produkt som tilldelar samma källa.
1. Ange lagerkvantitet = 1.
1. Ta en titt på produkten som skapats i steg 4 med *[!UICONTROL In-Store Delivery]* från butiken.
1. Skapa en faktura för ordern.
1. Ställ in produktkvantiteten till *0* och bli av med det.
1. Bokför följande API-begäran:

```
{
    "orderIds": [
        1
    ]
}
```

<u>Förväntade resultat</u>:

Redo för att hämta e-post har inte skickats.

<u>Faktiska resultat</u>:

API returnerar *Ordern är inte klar för hämtning*, men e-postmeddelandet skickas som klart för hämtning.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
