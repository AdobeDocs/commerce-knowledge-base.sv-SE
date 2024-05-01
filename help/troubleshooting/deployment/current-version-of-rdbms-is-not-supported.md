---
title: Felet "Aktuell version av RDBMS stöds inte" vid distribution
description: "Den här artikeln innehåller en lösning för när en distribution misslyckas och du får följande fel i distributionsloggen: *aktuell version av RDBMS stöds inte*."
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Felet &quot;Aktuell version av RDBMS stöds inte&quot; vid distribution

Den här artikeln innehåller en lösning för när en distribution misslyckas och du får följande fel i distributionsloggen: *aktuell version av RDBMS stöds inte*.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## Problem

Det här felmeddelandet betyder att den aktuella versionen av MariaDB inte längre stöds i den Adobe Commerce-version som du försöker uppgradera till, och att MariaDB måste uppgraderas till en kompatibel version.


<u>Steg som ska återskapas</u>:

Försök att distribuera.

<u>Förväntat resultat</u>:

Distributionen lyckades.

<u>Faktiskt resultat</u>:

Distributionen misslyckas med felmeddelande: *aktuell version av RDBMS stöds inte*.

## Orsak

Din version av MariaDB är inte kompatibel med den version av Adobe Commerce som du försöker uppgradera till.

## Lösning

Du måste uppgradera MariaDB-tjänsten till en kompatibel version innan du uppgraderar programmet.


För integreringsgrenen på Adobe Commerce om molninfrastruktur Pro-planarkitekturen (och alla grenar i Starter-arkitekturen) följer du [Konfigurera tjänst](https://devdocs.magento.com/cloud/project/services.html) i vår dokumentation för utvecklare.

Om du vill ha information om hur du arbetar med fasning och produktion i Adobe Commerce på Cloud Infrastructure Pro-planarkitekturen kan du [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om du vill att tjänsterna ska uppgraderas innan du distribuerar uppgraderingen av Adobe Commerce-versionen.


## Relaterad läsning

* [Bästa tillvägagångssätt för byggen och driftsättningen](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) i vår dokumentation för utvecklare.
* [Uppgradering av Adobe Commerce 2.3.5: kompakt till dynamiska tabeller](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) i vår kunskapsbas.
