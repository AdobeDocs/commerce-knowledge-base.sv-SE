---
title: Söka efter stora MySQL-tabeller
description: 'Om du vill identifiera de stora tabellerna ansluter du till databasen enligt beskrivningen i artikeln [Anslut till databasen](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) och kör följande kommando, där "project_id" är ditt projekt-ID i molnet:'
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Söka efter stora MySQL-tabeller

Om du vill identifiera de stora tabellerna ansluter du till databasen enligt beskrivningen i artikeln [Anslut till databasen](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) och kör följande kommando, där `project_id` är ditt projekt-ID i molnet:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Då visas en fullständig lista över tabeller och deras storlek. Du kan gå igenom listan och identifiera vilka tabeller som behöver åtgärdas på grund av den stora storleken.

## Relaterad läsning

[Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
