---
title: Kupong för engångsbruk används flera gånger, Adobe Commerce
description: Den här artikeln innehåller en lösning på problemet när kuponger med kundprisregel inte fungerar som de ska. Merchants skapar en kupong för engångsbruk och kunderna kan använda den flera gånger.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Kupong för engångsbruk används flera gånger, Adobe Commerce

Den här artikeln innehåller en lösning på problemet när kuponger med kundprisregel inte fungerar som de ska. Merchants skapar en kupong för engångsbruk och kunderna kan använda den flera gånger.


## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.4.3 och senare

## Problem

Merchants skapar en kupong för engångsbruk och kunderna kan använda den flera gånger.

<u>Steg som ska återskapas</u>:

1. Skapa en kupong och konfigurera kupongen för engångsbruk.
1. Gå till kassan.
1. Använd kupongen som du nyss skapade.
1. Gå till kassan igen och använd samma kupong.

<u>Förväntat resultat</u>:

Kupongen får bara användas en gång. Ett meddelande visas: *Kupongkoden COUPON_NAME är ogiltig*.

<u>Faktiskt resultat</u>:

Kupongen kan användas mer än en gång.


## Orsak

Handlare har inte `sales.rule.update.coupon.usage` kundens inställning och körning resulterar i felaktigt beteende.

## Lösning

Lägg till `sales.rule.update.coupon.usage` för `app/etc/env.php` -fil.

```php
...
    'cron_consumers_runner' =>
    array [
        'cron_run' => true,
        'max_messages' => 20000,
        'consumers' =>
        array [
            'sales.rule.update.coupon.usage'
        ]
    ],
...
```

Detaljerade anvisningar finns i [Hantera meddelandeköer > Konfiguration](https://devdocs.magento.com/guides/v2.4/config-guide/mq/manage-message-queues.html#configuration) i vår dokumentation för utvecklare.

## Relaterad läsning

[Översikt över meddelandeköer](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html) i vår dokumentation för utvecklare.
