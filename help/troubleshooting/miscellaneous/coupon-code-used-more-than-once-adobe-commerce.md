---
title: Kupong för engångsbruk används flera gånger, Adobe Commerce
description: Den här artikeln innehåller en lösning på problemet när kuponger med kundprisregel inte fungerar som de ska. Merchants skapar en kupong för engångsbruk och kunderna kan använda den flera gånger.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Kupongen får bara användas en gång. Ett meddelande visas: *Kupongkoden COUPON_NAME är inte giltig*.

<u>Faktiskt resultat</u>:

Kupongen kan användas mer än en gång.


## Orsak

Merchants har inte konfigurerat och kört `sales.rule.update.coupon.usage`-konsument vilket leder till felaktigt beteende.

## Lösning

Lägg till `sales.rule.update.coupon.usage`-konsumenten i filen `app/etc/env.php`.

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

Mer information finns i [Hantera meddelandeköer > Konfiguration](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues#configuration) i utvecklardokumentationen.

## Relaterad läsning

[Message Queues - översikt](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework) i utvecklardokumentationen.
