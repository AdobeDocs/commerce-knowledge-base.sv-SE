---
title: Uppgradering till B2B 1.5.2 misslyckas med SQL-syntaxfel eftersom funktionen REGEXP_LIKE saknas
description: I den här artikeln finns en snabbkorrigering för det problem där ett SQL-syntaxfel inträffar på grund av att funktionen REGEXP_LIKE saknas vid försök att uppdatera tabellen company_structure.
feature: B2B, Upgrade
role: Admin, Developer
exl-id: c5fe316c-99e3-482e-80b5-25aaae371230
source-git-commit: 04e17dfdf143e233eb2767064c1328990c899eda
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Uppgradering till B2B 1.5.2 misslyckas med SQL-syntaxfel eftersom funktionen REGEXP_LIKE saknas

>[!INFO]
>
>Om du får ett prestandaproblem när du uppgraderar modulen `Magento_Company` efter att ha uppdaterat till B2B 1.5.2 ska du använda den bifogade [ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip).
>
>Mer information finns i [Prestandaproblem i Magento_Company-moduluppgraderingen efter uppdatering B2B 1.5.2](/help/troubleshooting/installation-and-upgrade/magento-company-module-upgrade-performance-issue.md) i Adobe Commerce kunskapsbas.

I den här artikeln finns en snabbkorrigering för SQL-syntaxfelet som inträffar på grund av att funktionen `REGEXP_LIKE` saknas vid försök att uppdatera tabellen `company_structure`.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) 2.4.6-px + B2B 1.5.2 med [!DNL MariaDB] 10.6
* Adobe Commerce (alla distributionsmetoder) 2.4.7-px + B2B 1.5.2 med [!DNL MariaDB] 10.6

## Problem

Uppgraderingen till B2B version 1.5.2 misslyckas med ett SQL-syntaxfel på grund av att funktionen `REGEXP_LIKE` saknas vid försök att uppdatera tabellen `company_structure`.

<u>Förutsättningar</u>:

* MariaDB 10.6
* Adobe Commerce 2.4.6x eller 2.4.7x
* B2B version 1.5.0 eller 1.5.1

<u>Steg som ska återskapas</u>:

1. Tilldela ett företag till ett överordnat företag för att upprätta en företagshierarki. Mer information finns i [Hantera företagshierarkin](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) i Adobe Commerce B2B-guiden.
1. Uppgradera B2B till version 1.5.2.

<u>Förväntade resultat</u>:

Uppgraderingen har slutförts.

<u>Faktiska resultat</u>:

`bin/magento setup:upgrade` misslyckas med följande fel:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^123(/.+)?$'))
```

## Lösning

Så här löser du problemet:

1. Uppdatera B2B-modulen till version 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Använd den bifogade korrigeringen [ACSD-65540_B2B_1.5.2.zip](assets/ACSD-65540_B2B_1.5.2.zip). Mer information finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.
1. Kör `bin/magento setup:upgrade`.

### Tillämpa en korrigering med hjälp av molnkorrigeringar

Följ stegen nedan för Adobe Commerce om Cloud-infrastrukturer:

1. Uppdatera versionen av modulen `cloud-patches` till 1.1.5:

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Genomför och skicka ändringarna för att initiera omdistributionen. Mer information finns i [Använda korrigeringsfiler](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) i handboken för Adobe Commerce om molnet.
