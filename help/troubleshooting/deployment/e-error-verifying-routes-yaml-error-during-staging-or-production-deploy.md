---
title: 'E: Fel vid verifiering av vägar.yaml-fel under mellanlagrings- eller produktionsdistributionen'
description: 'I den här artikeln finns en lösning på problemet med molninfrastruktur, där du får felmeddelandet *"E: Error while verification route.yaml"* när du försöker distribuera projektet till förproduktionsmiljön.'
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E: Fel vid verifiering av vägar.yaml-fel under mellanlagrings- eller produktionsdistributionen

I den här artikeln finns en lösning på problemet med molninfrastruktur, där du får felmeddelandet *&quot;E: Error while verification route.yaml&quot;* när du försöker distribuera projektet till mellanlagrings- eller produktionsmiljön.

## Berörda versioner

* Adobe Commerce om molninfrastruktur, alla versioner

## Problem

<u>Steg som ska återskapas</u>:

Utlös en distribution genom att överföra koden till mellanlagrings- eller produktionsmiljön.

<u>Förväntat beteende</u>:

Distributionen har slutförts.

<u>Faktiskt beteende</u>:

Distributionen är blockerad och följande felmeddelande visas i loggen:

<pre>Distribuerar program Verifierar konfiguration E: Fel vid verifiering av route.yaml.
Följande domäner har konfigurerats för ditt kluster, men inga vägar har definierats i filen route.yaml:

- store1.example.com
- store2.example.com
- test-store.example.com

Med din nuvarande konfiguration route.yaml
  dessa domäner skulle INTE betjänas!

Om du vill fortsätta kan du läsa här för instruktioner om hur du felsöker:
 /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## Orsak

Det här felet inträffar om flödeskonfigurationen för eventuella ytterligare domäner som har lagts till i ditt projekt saknas i filen `routes.yaml`.

Som en del av uppgraderingen av Adobe Commerce självbetjäningsaktivering för konfiguration av självbetjäningsväg har vi lagt till en kontroll före distributionen för att säkerställa att alla domäner i ditt projekt har konfigurerade vägar i filen `routes.yaml`. Om någon domän saknar vägkonfiguration blockeras distributionen.

## Lösning

Du löser den blockerade distributionen genom att uppdatera filen `routes.yaml` och konfigurera vägar för domänerna som anges i felmeddelandet på något av följande sätt:

* Använd den patch som Adobe Commerce tillhandahåller under uppgraderingsprocessen.
* Lägg till den saknade vägkonfigurationen manuellt i filen `routes.yaml`.

### Metod 1: Använd patchen som tillhandahålls av Adobe Commerce

1. Leta efter en senaste Adobe Commerce-supportanmälan med titeln *Aktivera självbetjäningsfunktioner för &lt;project\_ID>.*
1. Följ instruktionerna i biljetten för att tillämpa korrigeringen, som uppdaterar vägkonfigurationen för din molnmiljö.
1. С implementera och push-implementera ändringarna för att omdistribuera projektet.

### Metod 2: Lägg till den saknade flödeskonfigurationen manuellt

1. Om du vill betjäna alla domäner i ditt projekt med samma flödeskonfiguration uppdaterar du filen `routes.yaml` och lägger till flödesmallar för standarddomänen och alla andra domäner i ditt projekt enligt följande exempel:

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. С implementera och implementera ändringarna för att omdistribuera projektet.

Detaljerade instruktioner om hur du uppdaterar vägkonfigurationen finns i [Cloud for Adobe Commerce > Konfigurera vägar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml) i utvecklardokumentationen.

>[!NOTE]
>
>Om projektkonfigurationen anger domäner som inte längre används följer du de här stegen för att ta bort dem från projektet så snart som möjligt: 1. Skicka en supportanmälan med en lista över domäner som ska tas bort från dina projektmiljöer. 2. När supportteamet har tagit bort domänerna uppdaterar du filen `routes.yaml` så att alla referenser till de föråldrade domänerna tas bort.
