---
title: Fel vid reflektionsundantag vid installation
description: I den här artikeln finns en lösning på Reflexion Exception-felet under installationen.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Fel vid reflektionsundantag vid installation

I den här artikeln finns en lösning på Reflexion Exception-felet under installationen.

## Information {#details}

Under installationen visas ett meddelande som liknar följande:

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## Lösning {#solution}

Rensa alla kataloger och filer under Adobe Commerce `var`-underkatalog och installera Adobe Commerce-programmet igen.

Ange följande kommandon som [Adobe Commerce-filsystemsägare](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) eller som en användare med `root` behörighet:

```bash
$ cd <your Magento install directory>/var
```

```bash
$ rm -rf var/cache/* di/* generation/* page_cache/*
```

### Redis {#redis}

Om du använder Redis och fortfarande får ett fel rensar du Redis-cachen enligt följande:

```bash
$ redis-cli FLUSHALL
```
