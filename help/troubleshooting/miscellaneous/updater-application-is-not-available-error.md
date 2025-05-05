---
title: Felet '"Updater application is not available"'
description: Den här artikeln handlar om lösningen på problemet med att uppdateringsprogrammet inte är tillgängligt som kan uppstå när du försöker uppdatera/installera Adobe Commerce lokalt med hjälp av webbinstallationsguiden.
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Felet &quot;Updater application is not available&quot;

Den här artikeln handlar om lösningen på problemet med att uppdateringsprogrammet inte är tillgängligt som kan uppstå när du försöker uppdatera/installera Adobe Commerce lokalt med hjälp av webbinstallationsguiden.

## Problem

Följande meddelande visas i beredskapskontrollen:

![Screen_Shot_2019-08-29_at_1.39.12_PM.png](assets/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

## Berörda produkter/versioner

* Adobe Commerce lokal 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Lösning

Du kan lösa det här problemet genom att kontrollera om det finns en `<magento_root>/update`-katalog som innehåller filer och underkataloger. Annars kan du läsa [Konfigurera uppdateraren](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/updater-application-is-not-available-error) i utvecklardokumentationen.
