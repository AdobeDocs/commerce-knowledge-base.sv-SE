---
title: Ta bort Magento Order Management (MOM)
description: I den här artikeln beskrivs hur du tar bort Magento Ordern Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Ta bort Magento Order Management (MOM)

1. Inaktivera MOM-integreringen genom att följa stegen i [Inaktivera eller aktivera integreringen](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration).
1. Inaktivera MOM-modulen genom att följa stegen i [Avinstallera moduler](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. Vi erbjuder API:t för att extrahera fullständiga orderdata. Du kan lära dig mer genom att läsa [orderdatabasen](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) i Adobe | Magento OMS Docs, som omfattar orderinformation (order_database). Använd [specifikationsavsnittet](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) i Adobe | Magento OMS Docs om du vill använda andra API:er för att extrahera olika informationstyper.
