---
title: Prestandaproblem i moduluppgraderingen Magento_Company efter uppdatering av B2B 1.5.2
description: Den här artikeln innehåller en snabbkorrigering för prestandaproblemet i Magento_Company-moduluppgraderingen efter uppdateringen av B2B 1.5.2, som åtgärdar den mycket långa bearbetningstiden för stora datamängder i tabellen company_structure.
feature: B2B, Upgrade
role: Admin, Developer
source-git-commit: d06f0045b4c4c1615bd3abec963eb17fdee93860
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Prestandaproblem i moduluppgraderingen Magento_Company efter uppdatering av B2B 1.5.2

Den här artikeln innehåller en snabbkorrigering för prestandaproblemet i moduluppgraderingen `Magento_Company` efter uppdateringen av B2B 1.5.2, som åtgärdar den mycket långa bearbetningstiden för stora datamängder (~100 000+ poster) i tabellen `company_structure`.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) 2.4.6-px + B2B 1.5.2
* Adobe Commerce (alla distributionsmetoder) 2.4.7-px + B2B 1.5.2
* Adobe Commerce (alla distributionsmetoder) 2.4.8 + B2B 1.5.2

## Problem

Uppgradering av modulen `Magento_Company` efter uppdatering till B2B 1.5.2 tar mycket lång tid när ett stort antal poster bearbetas (~100 000+) i tabellen `company_structure`.

<u>Förutsättningar</u>:

* ACSD-65540_B2B_1.5.2.patch bör installeras.
* Adobe Commerce 2.4.6 - 2.4.8
* B2B version 1.5.0, 1.5.1 eller B2B 1.5.2 med patchen ACSD-65540 installerad

<u>Steg som ska återskapas</u>:

1. Tilldela ett företag till ett överordnat företag för att upprätta en företagshierarki. Mer information finns i [Hantera företagshierarkin](https://experienceleague.adobe.com/sv/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) i Adobe Commerce B2B-guiden.
1. Uppgradera B2B till version 1.5.2.

<u>Förväntade resultat</u>:

Uppgraderingen har slutförts.

<u>Faktiska resultat</u>:

Det tar lång tid att uppgradera modulen `Magento_Company` om det finns många poster i tabellen `company_structure`.

## Lösning

Så här löser du problemet:

1. Uppdatera B2B-modulen till version 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Använd [ACSD-65540_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2.zip).

1. Använd den bifogade [ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip).
1. Kör `bin/magento setup:upgrade` när korrigeringen har tillämpats.

### Så här sätter du på plåstret

Zippa upp filen och se [Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) i vår kunskapsbas för support för instruktioner.

### Tillämpa en korrigering med hjälp av molnkorrigeringar

För Adobe Commerce-handlare i molnet följer du stegen nedan:

1. Uppdatera versionen av modulen för molnkorrigeringar till 1.1.5 för att installera patchen ACSD-65540_B2B_1.5.2.som distribueras som MCLOUD-13605.

   >[!NOTE]
   >
   >Om du vill kontrollera om korrigeringen redan är installerad kör du:
   > `./vendor/bin/magento-patches -n status | grep MCLOUD-13605`

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Lägg till patchen ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch i katalogen `m2-hotfixes`.
1. Genomför och skicka ändringarna för att initiera omdistribution och `bin/magento setup:upgrade`. Mer information finns i [Använda korrigeringsfiler](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) i handboken för Adobe Commerce om molnet.

## Relaterad läsning

* [Uppgradering till B2B 1.5.2 misslyckas med SQL-syntaxfel på grund av att funktionen REGEXP_LIKE saknas](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/sql-syntax-error-due-to-missing-regexp-like-function)
