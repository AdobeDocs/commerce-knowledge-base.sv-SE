---
title: 'Uppdatering av disposition misslyckas på Adobe Commerce: Inkompatibel argumenttyp'
description: Den här artikeln innehåller en lösning för när distributionen stoppas på grund av ett problem med kodkompilering. Problemet orsakas av en ny version av symfony/console-beroende (4.4.27, 4.4.28).
exl-id: ba2dd229-29f6-43e2-9467-8bd1bf59e6ef
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Det går inte att uppdatera disposition på Adobe Commerce: Inkompatibel argumenttyp

>[!NOTE]
>
>Problemet har nu åtgärdats i den senaste symfonversionen 4.4.29.

Den här artikeln innehåller en lösning för när distributionen stoppas på grund av ett problem med kodkompilering. Problemet orsakas av en ny version av symfony/console-beroende (4.4.27, 4.4.28).

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) och Magento Open Source:
   * 2.4.0, 2.4.0-p1, 2.4.1, 2.4.1-p1, 2.4.2, 2.4.2-p1, 2.4.2-p2, 2.4.3
   * 2.3.5, 2.3.5-p1, 2.3.5-p2, 2.3.6, 2.3.6-p1, 2.3.7, 2.3.7-p1
* Symfony/console-beroende (4.4.27, 4.4.28).

## Problem

En ny version av symfony/console-beroende (4.4.27, 4.4.28) gör att beroendekompileringsprocessen misslyckas.

<u>Steg som ska återskapas</u>:

När du installerar eller uppgraderar Adobe Commerce eller kör en uppdatering av en disposition misslyckas körningen med följande felmeddelande:
*Inkompatibel argumenttyp: Obligatorisk typ: int. Faktisk typ: sträng*

## Orsak

Problemet beror på att Adobe Commerce kärnkod inte är kompatibel med det senaste &quot;symfony/console&quot;-beroendet som släpptes i versionerna 4.4.27 och 4.4.28.

## Lösning

Problemet kommer att lösas automatiskt när en ny symfoni/konsolversion 4.2.29 släpps (förväntas i augusti 2021).

**Så här korrigerar du på en plats i Adobe Commerce:**

Adobe Commerce lokal 2.4.x

Kör följande kommando i CLI/Terminal:

``composer require symfony/console:">=4.4.0 <4.4.27 || ~4.4.29"``

Alla 2.3.5+ Adobe Commerce lokala handlare ska köra följande CLI-kommando:

``composer require symfony/console:"~4.1.0||~4.2.0||~4.3.0||>=4.4.0 <4.4.27 || ~4.4.29"``

**Så här korrigerar du Adobe Commerce i molninfrastrukturen:**

Kör ovanstående kommandon eller uppgradera till den senaste versionen av ECE-verktygen (ece-tools: 2002.1.7), som kommer att vara tillgänglig torsdagen den 29 juli. Anvisningar om hur du gör detta finns i [Cloud för Adobe Commerce > Uppdatera versionen för verktygen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) i utvecklardokumentationen.

Den fullständiga korrigeringen släpps i Adobe Commerce (alla distributionsmetoder) 2.4.4.

## Relaterad läsning

* Github: [2021-07-27 Dispositionsuppdatering Inkompatibel argumenttyp: Obligatorisk typ: int. Faktisk typ: sträng ](https://github.com/magento/magento2/issues/33595)
