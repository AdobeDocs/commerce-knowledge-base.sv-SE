---
title: Det går inte att klona GitHub-databasen i Magento
description: I den här artikeln finns en korrigering för när du inte kan klona GitHub-databasen i Magento.
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# Det går inte att klona GitHub-databasen i Magento

I den här artikeln finns en korrigering för när du inte kan klona GitHub-databasen i Magento.

## Detalj {#detail}

Felet liknar följande:

```terminal
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## Lösning {#solution}

Överför din SSH-nyckel till GitHub enligt beskrivningen på [hjälpsidan för GitHub](https://help.github.com/articles/generating-ssh-keys) .
