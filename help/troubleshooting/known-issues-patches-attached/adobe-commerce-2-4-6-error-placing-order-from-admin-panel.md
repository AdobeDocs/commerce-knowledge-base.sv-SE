---
title: Adobe Commerce 2.4.6 error placing order from Admin panel
description: Den här artikeln innehåller en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.4.6 när du fastnar i butiksvalet efter att du har gjort en beställning från Commerce Admin-panelen.
feature: Admin Workspace
role: Developer
exl-id: b30be5a5-3681-41db-9040-3624faed7c46
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Adobe Commerce 2.4.6 error placing order from Admin panel

Den här artikeln innehåller en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.4.6 när du fastnar i butiksvalet efter att du har gjort en beställning från Commerce Admin-panelen.

## Problem

När du gör en beställning från Admin-panelen fastnar du i valet av butik.

<u>Steg som ska återskapas</u>

1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Orders]** och välj en kund för att skapa en order.
2. Välj butik för att placera beställningen från butiksväljaren.

<u>Förväntat resultat</u>

När du har valt butik kan du slutföra beställningen.

<u>Faktiskt resultat:</u>

När du har valt butiken omdirigeras du tillbaka till butiksväljarsidan och du kan inte skapa en order.

## Lappa

Klicka på följande länk för att hämta patchen.

[Hämta ACSD-52277_2.4.6.patch](assets/ACSD-52277_2.4.6.patch.zip)

### Kompatibla Adobe Commerce-versioner

Korrigeringen skapades för och är kompatibel med Adobe Commerce i molninfrastrukturen och Adobe Commerce lokalt 2.4.6 och 2.4.6-p1.

## Så här sätter du på plåstret

* Instruktioner om hur du använder korrigeringsfiler för Adobe Commerce i molninfrastrukturen finns i [Tillämpa korrigeringsfiler](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i vår Commerce om molninfrastrukturguide.
* Anvisningar om hur du tillämpar korrigeringsfiler för Adobe Commerce lokalt finns i [Tillämpa korrigeringsfiler](/docs/commerce-operations/upgrade-guide/patches/apply.html?lang=en#composer) i Commerce uppgraderingshandbok.
