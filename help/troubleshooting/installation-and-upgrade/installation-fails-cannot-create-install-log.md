---
title: Installationen misslyckades; det går inte att skapa install.log
description: Den här artikeln innehåller en korrigering för en misslyckad installation eftersom installationsguiden inte skapar "install.log" under installationen.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Installationen misslyckades; det går inte att skapa install.log

Den här artikeln innehåller en korrigering för en misslyckad installation eftersom installationsguiden inte skapar `install.log` under installationen.

## Problem

Om du kör Adobe Commerce-processer samtidigt kan det uppstå problem när installationsloggen skapas. (Exempel: två olika installationer på olika fliksidor.)

## Orsak

Installation-fails-cannot-create-install.log
Granska din inställning för `open_basedir` i `php.ini`. Installationsguiden använder PHP-anropet [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) för att hämta värdet för den tillfälliga katalogen. Om [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) är inställd på att neka anslutningar till en katalog som anges av `sys_get_temp_dir` misslyckas installationen.
Granska din inställning för `open_basedir` i `php.ini`. Installationsguiden använder PHP-anropet [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) för att hämta värdet för den tillfälliga katalogen. Om [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) är inställd på att neka anslutningar till en katalog som anges av `sys_get_temp_dir` misslyckas installationen.


## Lösning

Du löser problemet genom att ändra värdet för `open_basedir` och starta om webbservern.

Om du är osäker på hur du ska ändra det här värdet gör du så här:

1. Om du inte redan har gjort det skapar du [phpinfo.php](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/optional-software).
1. Ange följande URL i webbläsarens adress- eller platsfält: `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. Leta efter platsen för `php.ini`.     `php.ini` anges vanligtvis som **Inläst konfigurationsfil** i det resultat som visas.
1. Som användare med rotbehörighet öppnar du `php.ini` i en textredigerare.
1. Leta reda på värdet för `open_basedir` och ändra det.
1. Spara ändringarna i `php.ini`.
1. Starta om webbservern.
