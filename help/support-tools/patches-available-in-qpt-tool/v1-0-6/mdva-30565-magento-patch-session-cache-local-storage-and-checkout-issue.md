---
title: 'MDVA-30565: problem med lokal lagring och utcheckning av sessionscache'
description: MDVA-30565-korrigeringen löser problemet med lokal lagring och utcheckning av sessionscache. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat.
exl-id: f0693f0c-fc6b-44af-a6a0-ebfa973bca65
feature: Cache, Checkout, Orders, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-30565: problem med lokal lagring och utcheckning av sessionscache

MDVA-30565-korrigeringen löser problemet med lokal lagring och utcheckning av sessionscache. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce om molninfrastruktur 2.3.3-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundvagnsobjekt kan fortfarande visas på kundvagnssidan när en kundsession tar slut. Detta orsakar ett fel i leveransmetoden för beräkning om det inte finns några leveransmetoder tillgängliga för gästutcheckning.

<u>Steg som ska återskapas</u>:

1. Aktivera beständig kundvagn i Commerce Admin. (**Aktivera beständighet** = &quot;*Ja*&quot;)
1. Logga in som kund i förgrunden. Detta skapar `persistent_shopping_cart` cookie och initierar en beständig session.
1. Lägg en produkt i kundvagnen.
1. Vänta tills tidsgränsen för klientsessionen har nåtts eller ta bort `PHPSESSID` cookie.
1. Nu är du gästanvändare, men om du går till kundvagnen kan du fortfarande se produkten som lagts till som inloggad kund.
1. Ta bort produkten från vagnen så är vagnen tom. Du ser att Adobe Commerce tar bort `persistent_shopping_cart` cookie i den här händelsen.
1. Lägg en ny produkt i kundvagnen och gå till kundvagnen.
1. Nu visas det i webbläsarkonsolen `V1/guest-carts/4/estimate-shipping-methods` begäran returnerar nu ett 404-svar med ett meddelande `{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}`

<u>Förväntade resultat</u>:

Begäran om beräknad leveransmetod returnerar korrekta resultat.

<u>Faktiska resultat</u>:

Begäran om beräknad leveransmetod misslyckas med ett fel som: &quot;*Det finns tyvärr inga offerter för den här beställningen just nu.*&quot;

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
