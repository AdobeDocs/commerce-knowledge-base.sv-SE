---
title: Vid installationen visas ett allvarligt SUB-fel
description: I den här artikeln finns en korrigering för ett allvarligt SUB-fel under installationen.
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Vid installationen visas ett allvarligt SUB-fel

I den här artikeln finns en korrigering för ett allvarligt SUB-fel under installationen.

## Problem

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## Lösning

Kontrollera att du har installerat alla [nödvändiga PHP-tillägg](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/php-settings).
