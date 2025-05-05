---
title: Vid installationen visas en varning om PHP-datum
description: I den här artikeln finns en fix för en PHP-datumvarning under installationen.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# Vid installationen visas en varning om PHP-datum

I den här artikeln finns en fix för en PHP-datumvarning under installationen.

## Information {#details}

Under installationen visas följande meddelande:

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### Lösning {#solution}

Kontrollera PHP-tidszonsinställningen noggrant. Se [Installationshandbok > PHP-inställningar](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/php-settings) i utvecklardokumentationen.
