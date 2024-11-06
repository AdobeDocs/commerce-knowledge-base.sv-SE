---
title: Auto_increment-variabeln database inställd på "3" Adobe Commerce på vår molnprofessionella arkitektur
description: Detta är det förväntade beteendet för Adobe Commerce i molninfrastrukturproffsens arkitekturlösningar på grund av 3-nodarkitekturen och kan inte ändras.
exl-id: ea478cbc-2dc2-41c9-8ea7-7e2f308e5948
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Auto_increment-variabeln database inställd på &quot;3&quot; Adobe Commerce på vår molnprofessionella arkitektur

Detta är det förväntade beteendet för Adobe Commerce i molninfrastrukturproffsens arkitekturlösningar på grund av 3-nodarkitekturen och kan inte ändras.

Galera-databaskluster används, som är ett databaskluster med en MariaDB MySQL-databas per nod med en inställning för automatisk ökning på tre för unika ID:n i varje databas.

<u>Varför separeras/ökas inte alltid det inkrement-ID som används i Pro-kluster med 3?</u>

Det inkrement-ID som används i kluster separeras/ökas inte alltid med 3 på grund av hur Galera fungerar.

Var och en av de tre servrarna hanterar sitt eget ID-utrymme, och den ökning som används beror på vilken MySQL-huvuddatabasserver (beroende på relativ inläsning) som är den varierande luckan.
Om du använder SSH för varje nod och ansluter till den lokala MySQL-instansen som körs på den noden med port 3307 (istället för att proxideras till &quot;main&quot; på standardport 3306) visas följande bild:

![auto_increment](assets/auto_increment_id.png)

Om den valda huvudsidan är nod 1 där `auto_increment_offset = 1`, ökas ID:t med 1. Om en ny huvudnod markeras vid ett senare tillfälle, t.ex. nod 3 där `auto_increment_offset = 3`, ökas den med 3 i stället.

## Användbara länkar

Läs mer i vår utvecklardokumentation:

* [Cloud för Adobe Commerce > Pro-arkitektur > Säkerhetskopiering och katastrofåterställning](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [Cloud för Adobe Commerce > Installationskrav: databas](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview)
