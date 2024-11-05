---
title: Bearbetningsfel i Magento Order Management System (OMS) för Adobe Commerce
description: Den här artikeln innehåller en lösning på problemet när du får ett "getMode()"-fel i CLI som kör "bin/magento oms:messages:process" i OMS (Magento Order Management System) för Adobe Commerce.
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Bearbetningsfel i Magento Order Management System (OMS) för Adobe Commerce

Den här artikeln innehåller en lösning på problemet när du får ett `getMode()`-fel i CLI som kör `bin/magento oms:messages:process` i OMS (Magento Order Management System) för Adobe Commerce.

## Berörda produkter och versioner

Detta fel inträffar när MCOM Connector version 3.1.1 och 3.2.0 används. Det löses i MCOM Connector 3.3.0. Den är inte specifik för en MDC- eller MOM-version.

## Problem

När följande kommando körs i CLI:

`bin/magento oms:messages:process`

Ett felmeddelande som liknar följande visas i CLI:

```
<project-id>@<project-id>:~$ php bin/magento oms:messages:process

Processing messages...

PHP Fatal error:Uncaught Error: Call to a member function getMode()
on null in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php:64

Stack trace:

  #0 [internal function]: Magento\InventoryMessageBus\Handler\OnAggregateStockUpdatedSubscriber->onUpdated(Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #1 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(81):
  call_user_func(Array, Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #2 [internal function]: Magento\ServiceBus\Message\SingleMessageProcessor->Magento\ServiceBus\Message\\{closure}(Array)

  #3 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(86):
  array_map(Object(Closure), Array)

  #4 /app/<project-id>/vendor/magento/module-service-bus/Message/Processor.php(110):
  Magento\ServiceBus\Message\SingleMessageProcessor->process(Object(Magento\CommonMessageBus\Message\Message))

  #5 /app/t in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php
  on line 64
```

## Orsak

Â
Detta inträffar när anslutningsprogrammet försöker bearbeta `magento.inventory.source_management` meddelanden. Anslutaren försöker bearbeta dessa meddelanden som om de vore ett `magento.inventory.source_stock_management.update`-meddelande som kräver ett lägesvärde. Eftersom det inte finns något läge i `magento.inventory.source_mangement`-meddelandena inträffar felet.

## Lösning

Du löser problemet genom att köra följande [!DNL SQL]-sats i CLI som tar bort alla poster i tabellen `mcom_api_messages`:

`delete from mcom_api_messages;`

## Relaterad läsning

* OMS Docs [OMS Connector Setup Tutorial](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/)
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
