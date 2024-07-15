---
title: Kända fel som påverkar xdebug-installationen
description: Den här artikeln innehåller en lösning för när du får ett undantagsfel när du använder det valfria PHP-tillägget "xdebug".
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Kända fel som påverkar xdebug-installationen

Den här artikeln innehåller en lösning för när du får ett undantagsfel när du använder det valfria PHP-tillägget `xdebug`.

* Under installationen
* Åtkomst till antingen Commerce Admin eller Store efter en slutförd installation

Exempelundantag:

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

Du kan lösa problemet genom att:

* Inaktivera tillägget `xdebug`.
* Ange värdet `xdebug.max_nesting_level` till 200 eller mer. Mer information finns i [xdebug-dokumentation](http://xdebug.org/docs/basic#max_nesting_level).

När du har ändrat konfigurationen av eller inaktiverat `xdebug` startar du om Apache:

* CentOS: `sudo service httpd restart`
* Ubuntu: `sudo service apache2 restart`
