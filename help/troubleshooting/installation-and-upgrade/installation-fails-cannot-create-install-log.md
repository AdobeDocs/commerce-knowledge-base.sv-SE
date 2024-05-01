---
title: Installationen misslyckades; det går inte att skapa install.log
description: Den här artikeln innehåller en korrigering för en misslyckad installation eftersom installationsguiden inte skapar "install.log" under installationen.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Installationen misslyckades; det går inte att skapa install.log

Den här artikeln innehåller en korrigering för en misslyckad installation eftersom installationsguiden inte skapar `install.log` under installationen.

## Problem

Om du kör Adobe Commerce-processer samtidigt kan det uppstå problem när installationsloggen skapas. (Exempel: två olika installationer på olika fliksidor.)

## Orsak

Installation-fails-cannot-create-install.log Kontrollera inställningen för `open_basedir` in `php.ini`. Installationsguiden använder [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP-anrop för att hämta värdet för den tillfälliga katalogen. If [open\_basedier](http://php.net/manual/en/ini.core.php#ini.open-basedir) är inställt på att neka anslutningar till en katalog som anges av `sys_get_temp_dir`, misslyckas installationen.
Granska inställningarna för `open_basedir` in `php.ini`. Installationsguiden använder [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP-anrop för att hämta värdet för den tillfälliga katalogen. If [open\_basedier](https://php.net/manual/en/ini.core.php#ini.open-basedir) är inställt på att neka anslutningar till en katalog som anges av `sys_get_temp_dir`, misslyckas installationen.


## Lösning

Du löser problemet genom att ändra värdet för `open_basedir` och starta om webbservern.

Om du är osäker på hur du ska ändra det här värdet gör du så här:

1. Om du inte redan har gjort det skapar du [phpinfo.php](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo).
1. Ange följande URL i webbläsarens adress- eller platsfält: `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. Sök efter platsen för `php.ini`.     `php.ini` anges vanligtvis som **Inläst konfigurationsfil** i de resultat som visas.
1. Öppna som en användare med rotbehörighet `php.ini` i en textredigerare.
1. Leta reda på värdet för `open_basedir` och ändra det.
1. Spara ändringarna i `php.ini`.
1. Starta om webbservern.
