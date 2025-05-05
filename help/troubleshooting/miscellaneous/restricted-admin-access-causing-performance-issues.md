---
title: Begränsad administratörsåtkomst som orsakar prestandaproblem
description: Den här artikeln innehåller lösningar för när prestanda påverkas negativt av att du använder [Admin roles with role scope limited by website](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) i vår användarhandbok.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Begränsad administratörsåtkomst som orsakar prestandaproblem

Den här artikeln innehåller lösningar för när prestanda påverkas negativt av att du använder [administratörsroller med rollomfång som begränsas av webbplatsen](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) i användarhandboken.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x

## Problem

När en Admin-användare, med rollomfånget begränsat av webbplatsen, utför åtgärder på Admin-panelen (inklusive inloggning, spara produkter och så vidare), återskapar Adobe Commerce den lagrade cachen. Ombyggnad av cachen påverkar prestandan negativt och kan leda till ett driftstopp på webbplatsen, särskilt under kontorstid och/eller vid hög trafik.

Problemet har åtgärdats i Adobe Commerce 2.2.10 och 2.3.3.

## Lösning

Följande alternativ är för att undvika problemet:

* Uppgradera Adobe Commerce till 2.2.10 eller 2.3.3. (Mer information finns i [Uppgradera Adobe Commerce för molninfrastruktur](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) i utvecklardokumentationen).
* Undvik, om möjligt, att begränsa användarrollens omfång per webbplats.
* [Skicka en Magento-supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att begära en korrigering, om en sådan finns tillgänglig.

## Relaterad läsning

* [Användarroller](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/user-accounts/permissions-user-roles) i vår användarhandbok.
