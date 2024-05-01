---
title: Söka efter stora MySQL-tabeller
description: '"För att identifiera de stora tabellerna ansluter du till databasen enligt beskrivningen i artikeln [Anslut till databasen](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) och kör följande kommando, där "project_id" är ditt projekt-ID i molnet:"'
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Söka efter stora MySQL-tabeller

Identifiera de stora tabellerna genom att ansluta till databasen enligt beskrivningen i [Anslut till databasen](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) och kör följande kommando, där `project_id` är ditt projekt-ID i molnet:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Då visas en fullständig lista över tabeller och deras storlek. Du kan gå igenom listan och identifiera vilka tabeller som behöver åtgärdas på grund av den stora storleken.
