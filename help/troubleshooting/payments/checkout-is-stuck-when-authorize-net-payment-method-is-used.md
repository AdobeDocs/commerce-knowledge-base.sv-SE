---
title: Utcheckningen fastnar när Authorize.net betalningsmetod används
description: Den här artikeln innehåller en förklaring och en korrigering av Adobe Commerce 2.3.X-problemet där utcheckningen fastnar om Authorize.net används, med felmeddelandet *'Cannot read property 'length' of null'* i webbläsarkonsolloggen.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Utcheckningen fastnar när Authorize.net betalningsmetod används

I den här artikeln ges en förklaring och en korrigering för Adobe Commerce 2.3.X-problemet där utcheckningen fastnar om Authorize.net används med *Det går inte att läsa egenskapen length för null* felmeddelande i webbläsarkonsolloggen.

## Berörda produkter och versioner

* Adobe Commerce 2.3.X

>[!NOTE]
>
>Adobe Commerce Authorize.Net-betalningsintegreringen har tagits bort sedan 2.3.4 och har tagits bort helt i 2.4.0. Använd ett tillägg som passar dina behov från [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/) i stället.

## Problem

<u>Steg som ska återskapas</u>

1. Konfigurera Authorize.net i Commerce Admin.
1. Gå till butiken.
1. Lägg en produkt i kundvagnen och fortsätt till kassan.
1. Välj Authorize.net som betalningsmetod.
1. Klicka **Montera beställning**.

<u>Förväntat resultat</u>

Authorize.net iframe läses in.

<u>Faktiskt resultat</u>

Ajax-rotationsrutan visas och sidan läses aldrig in. Följande JS-fel visas i webbläsarkonsolloggen: *&#39;Uncaught TypeError: Cannot read property &#39;length&#39; of null at b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;*

## Orsak

En av de vanligaste orsakerna till problemet är att den offentliga klientnyckeln inte har angetts i Authorize.Net-konfigurationen i Commerce Admin.

## Lösning

Under **Lager** > **Inställningar** > **Konfiguration** > **Försäljning** > **Betalningsmetoder**, i **Authorize.net** kontrollerar du om värdet anges i **Offentlig klientnyckel** fält. Om det är tomt anger du nyckelvärdet från ditt Authorize.Net-handelskonto.

Rensa cacheminnet genom att köra ändringarna

```bash
bin/magento cache:clean
```
