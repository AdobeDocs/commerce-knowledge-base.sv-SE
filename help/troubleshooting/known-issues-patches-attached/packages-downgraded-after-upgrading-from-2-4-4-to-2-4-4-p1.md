---
title: Paket som nedgraderats efter uppgradering från 2.4.4 till 2.4.4-p1
description: Den här artikeln innehåller en snabbkorrigering för problemet när handlare i version 2.4.4 kör kommandot "Composer update" och sedan nedgraderas paketen (modulerna) som listas nedan till sina tidigare versioner som inte är kompatibla med version 2.4.4 och endast ska användas med version 2.4.5 och senare.
exl-id: 4ebdbcd7-6905-4647-b071-1e4413455f38
feature: Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Paket som nedgraderats efter uppgradering från 2.4.4 till 2.4.4-p1

Den här artikeln innehåller en snabbkorrigering för problemet när handlare i version 2.4.4 kör `composer update` och sedan nedgraderas de paket (moduler) som anges nedan till sina tidigare versioner som inte är kompatibla med version 2.4.4 och som endast ska användas med version 2.4.5 och senare.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur 2.4.4
* Adobe Commerce lokal 2.4.4
* Magento Open Source 2.4.4

## Problem

Det finns två scenarier för hur problemet kan uppstå och hur det kan reproduceras:

### Scenario 1

<u>Steg som ska återskapas</u>:

Vid uppgradering från 2.4.4 till 2.4.4-p1 finns det ett antal paket (moduler) som nedgraderas med liknande utdata:

```text
Downgrading magento/module-adobe-ims (2.1.4 => 2.1.3)
Downgrading magento/module-adobe-ims-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-admin-ui (1.3.2 => 1.3.1)
Downgrading magento/module-adobe-stock-client-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-image (1.3.3 => 1.3.2)
Downgrading magento/module-adobe-stock-image-admin-ui (1.3.3 => 1.3.2)
Downgrading magento/module-banner-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-inventory (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-advanced-checkout (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-api (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-bundle-product (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-catalog-api (1.3.3 => 1.3.2)
Downgrading magento/module-inventory-configurable-product-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-configurable-product-frontend-ui (1.0.3 => 1.0.2)
Downgrading magento/module-inventory-import-export (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-in-store-pickup-admin-ui (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-frontend (1.1.3 => 1.1.2)
Downgrading magento/module-inventory-in-store-pickup-graph-ql (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-sales-admin-ui (1.1.3 => 1.1.2-p1)
Downgrading magento/module-inventory-in-store-pickup-shipping (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-low-quantity-notification (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-low-quantity-notification-api (1.2.2 => 1.2.1-p1)
Downgrading magento/module-inventory-requisition-list (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-admin-ui (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-api (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-shipping-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-source-selection-api (1.4.2 => 1.4.1-p1)
Downgrading magento/module-inventory-wishlist (1.0.2 => 1.0.1)
Downgrading magento/module-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-re-captcha-checkout-sales-rule (1.1.1 => 1.1.0)
Downgrading magento/module-re-captcha-customer (1.1.3 => 1.1.2)
Downgrading magento/module-re-captcha-frontend-ui (1.1.3 => 1.1.2)
Downgrading magento/module-staging-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-two-factor-auth (1.1.4 => 1.1.3)
Removing magento/module-admin-adobe-ims (100.4.0)
```

<u>Förväntade resultat</u>:

Uppgraderingen från version 2.4.4 till 2.4.4-p1 resulterar i rätt paket (moduler) för version 2.4.4-p1.

<u>Faktiska resultat</u>:

Under uppgraderingen från version 2.4.4 till 2.4.4-p1 nedgraderas dessa paketversioner (modulversioner), men meddelandena kan ignoreras och funktionaliteten påverkas inte.

### Scenario 2

<u>Steg som ska återskapas</u>:

När 2.4.4 handlare kör `composer update` och därefter samma paket (moduler) som anges ovan i **Scenario 1** uppgraderas till sina nyare versioner som endast är kompatibla med version 2.4.5 och inte ska användas med version 2.4.4.

<u>Förväntade resultat</u>:

Uppgraderingen från version 2.4.4 till 2.4.4-p1 resulterar i rätt paket (moduler) för version 2.4.4-p1.

<u>Faktiska resultat</u>:

Paket (moduler) nedgraderas efter uppgradering från version 2.4.4 till 2.4.4-p1.

## Tillfällig lösning 1: Laga

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk: [Hämta ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip)

## Kompatibla versioner av Adobe Commerce och Magento Open Source:

Korrigeringen skapades för:

* Adobe Commerce i molninfrastruktur 2.4.4
* Adobe Commerce lokal 2.4.4
* Magento Open Source 2.4.4

>[!NOTE]
>
>Korrigeringen är inte kompatibel med andra versioner och utgåvor av Adobe Commerce och Magento Open Source.

## Så här använder du patchen

Använd det kopplade basskriptet [ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip) som en tillfällig lösning på problemet.

**Exakta anvisningar om hur du använder skriptet:**

### På Adobe Commerce om molninfrastruktur:

1. Hämta basskriptfilen `ACPLTSRV-2017-fix.sh` till din lokala utcheckning av din molnkodbas.
1. Kör bash-skriptfilen `ACPLTSRV-2017-fix.sh` om du vill ändra dispositionsfilerna lokalt.
1. Lägg till och implementera de ändrade dispositionsfilerna i Git-databasen.

### På Adobe Commerce eller Magento Open Source, lokalt:

1. Placera det basala skriptet `ACPLTSRV-2017-fix.sh` i `root` mapp för din Adobe Commerce/Magento Open Source 2.4.4-installation (samma mapp som `composer.json`).
1. Kör det grundläggande skriptet med en `apply` argument för att låsa berörda paket (moduler) till version 2.4.4:

   ```bash
   sh ACPLTSRV-2017-fix.sh apply
   ```

1. Kör dispositionen uppdaterad för att installera låsta paket (moduler).
1. När du är redo att uppgradera till 2.4.5 eller 2.4.4-p1 kör du skriptet med en `rollback` argument:

   ```bash
   sh ACPLTSRV-2017-fix.sh rollback
   ```

   Om du hoppar över det här steget uppstår uppgraderingsfel på grund av att paketkraven (modulerna) är i konflikt.
1. När du är klar med stegen ovan kan du börja uppgradera.

## Tillfällig lösning 2

Den andra lösningen på problemet är inte att köra `composer update` utan argument.
