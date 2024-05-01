---
title: Använda en kompositkorrigering från Adobe
description: I den här artikeln beskrivs hur du använder en kompositkorrigering för Adobe Commerce lokalt, Adobe Commerce i molninfrastrukturen och Magento Open Source.
exl-id: a9301ad8-1d4b-49f5-b679-758624928219
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Använda en kompositkorrigering från Adobe

I den här artikeln beskrivs hur du använder en kompositkorrigering för Adobe Commerce lokalt, Adobe Commerce i molninfrastrukturen och Magento Open Source.

>[!WARNING]
>
>Vi rekommenderar att du använder och testar korrigeringsfilen i mellanlagrings-/integreringsmiljön innan du använder den i produktionen. Vi rekommenderar även att du nyligen har säkerhetskopierat innan du ändrar något.

## Så här använder du en kompositkorrigering för Adobe Commerce i molninfrastrukturen {#cloud}

1. Om du inte har någon katalog med namnet `m2-hotfixes` i projektets rot skapar du en.
1. Kopiera `%patch_name%.composer.patch` filer till `m2-hotfixes` katalog.
1. Lägg till, implementera och skicka dina kodändringar:

   ```git
   git add -A
   ```

   ```git
   git commit -m "Apply %patch_name%.composer.patch patch"
   ```

   ```git
   git push origin
   ```

Mer information om hur du använder korrigeringsfiler i molnprojekt finns i [Tillämpa patchar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

### Använda en kompositkorrigering för Adobe Commerce lokalt och Magento Open Source {#commerce}

1. Överför patchen till Adobe Commerce lokala katalog eller Magento Open Source-rotkatalog.
1. Kör följande SSH-kommando:

   ```bash
   patch -p1 < %patch_name%.composer.patch
   ```

   (Om ovanstående kommando inte fungerar kan du försöka med att använda `-p2` i stället för `-p1` )

1. Uppdatera cacheminnet i administratören under **System** > **Cachehantering**.
