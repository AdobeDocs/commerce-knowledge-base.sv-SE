---
title: Begränsad administratörsåtkomst som orsakar prestandaproblem
description: Den här artikeln innehåller lösningar för när prestanda påverkas negativt av att du använder [Admin roles with role scope limited by website](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) i vår användarhandbok.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Begränsad administratörsåtkomst som orsakar prestandaproblem

Den här artikeln innehåller lösningar för när prestanda påverkas negativt av att använda [Administratörsroller med rollomfång begränsat av webbplats](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) i vår användarhandbok.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x

## Problem

När en Admin-användare, med rollomfånget begränsat av webbplatsen, utför åtgärder på Admin-panelen (inklusive inloggning, spara produkter och så vidare), återskapar Adobe Commerce den lagrade cachen. Ombyggnad av cachen påverkar prestandan negativt och kan leda till ett driftstopp på webbplatsen, särskilt under kontorstid och/eller vid hög trafik.

Problemet har åtgärdats i Adobe Commerce 2.2.10 och 2.3.3.

## Lösning

Följande alternativ är för att undvika problemet:

* Uppgradera Adobe Commerce till 2.2.10 eller 2.3.3. (för instruktioner, se [Uppgradera Adobe Commerce på molninfrastruktursversionen](https://devdocs.magento.com/guides/v2.3/cloud/project/project-upgrade.html) i vår dokumentation för utvecklare).
* Undvik, om möjligt, att begränsa användarrollens omfång per webbplats.
* [Skicka en supportanmälan till Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), för att begära en korrigering, om den är tillgänglig.

## Relaterad läsning

* [Användarroller](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html) i vår användarhandbok.
