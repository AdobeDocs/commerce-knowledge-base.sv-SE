---
title: Ta bort Magento Order Management (MOM)
description: I den här artikeln beskrivs hur du tar bort Magento Ordern Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Ta bort Magento Order Management (MOM)

1. Inaktivera MOM-integreringen genom att följa stegen i [Inaktivera eller aktivera integreringen](/docs/commerce-admin/systems/integrations/mcom.html#disable-or-enable-the-integration).
1. Inaktivera MOM-modulen genom att följa stegen i [Avinstallera moduler](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. Vi erbjuder API:t för att extrahera fullständiga orderdata. Du kan lära dig mer genom att läsa [orderdatabasen](https://omsdocs.magento.com/specifications/#magento.sales.order_repository) i Adobe | Magento OMS Docs, som omfattar orderinformation (order_database). Använd [specifikationsavsnittet](https://omsdocs.magento.com/specifications/#services) i Adobe | Magento OMS Docs om du vill använda andra API:er för att extrahera olika informationstyper.
