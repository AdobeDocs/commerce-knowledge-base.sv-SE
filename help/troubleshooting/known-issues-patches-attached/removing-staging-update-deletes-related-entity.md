---
title: Tar bort mellanlagringsuppdatering tar bort relaterad entitet
description: Den här artikeln innehåller en patch för det kända Adobe Commerce 2.2.3-problemet som rör enheten (kategori, CMS-sida osv.) tas bort när den relaterade schemauppdateringen tas bort.
exl-id: 91138ac1-916e-4dd1-bad5-892524fdd9e1
feature: CMS, Cache, Categories, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Tar bort mellanlagringsuppdatering tar bort relaterad entitet

Den här artikeln innehåller en patch för det kända Adobe Commerce 2.2.3-problemet som rör enheten (kategori, CMS-sida osv.) tas bort när den relaterade schemauppdateringen tas bort.

>[!NOTE]
>
>Problemet har åtgärdats i Adobe Commerce 2.2.6.

## Problem

När du tar bort en aktiv schemauppdatering mellan dess start- och slutdatum tas även den relaterade entiteten (kategori, underkategori, CMS-sida) bort.

<u>Steg som ska återskapas (med kategorier)</u>:

1. Logga in på Commerce Admin.
1. Skapa en ny underkategori under **Katalog** > **Kategorier**.
1. Skapa en ny mellanlagringsuppdatering med start- och sluttiden.
1. Vänta tills uppdateringen har installerats. Det är starttiden.
1. Ta bort uppdateringen med länken **Visa/redigera**.

<u>Förväntade resultat</u>:

Uppdateringen tas bort och underkategorin finns fortfarande i Admin.

<u>Faktiska resultat</u>:

Uppdateringen och underkategorin tas bort.

## Lösning

Tillämpa den korrigering som anges i den här artikeln och rensa cacheminnet som körs

```bash
bin/magento
  cache:clean
```

## Lappa

Patcherna är kopplade till den här artikeln. Om du vill hämta en patch bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på motsvarande länk:

* [Hämta MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-11059_EE_2.2.3_COMPOSER_v1.patch.zip)
* [Hämta MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-23505_EE_2.2.4_COMPOSER_v1.patch.zip)
* [Hämta MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch](assets/MDVA-12158_EE_2.2.5_COMPOSER_v2.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Patcharna skapades för:

* MDVA-1059\_EE\_2.2.3\_COMPOSER\_v1.patch skapades för Adobe Commerce (alla distributionsmetoder) 2.2.3
* MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch skapades för Adobe Commerce (alla distributionsmetoder) 2.2.4
* MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch skapades för Adobe Commerce (alla distributionsmetoder) 2.2.5

Patchen MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce lokal 2.2.0-2.2.2
* Adobe Commerce om molninfrastruktur 2.2.0-2.2.3

Patchen MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce lokal 2.1.0-2.1.18, 2.2.0-2.2.3
* Adobe Commerce om molninfrastruktur 2.1.0-2.1.18, 2.2.0-2.2.3

Patchen MDVA-23505\_EE\_2.2.5\_COMPOSER\_v1.patch är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce om molninfrastruktur 2.2.5

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Bifogade filer
