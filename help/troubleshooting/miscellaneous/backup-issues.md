---
title: Säkerhetskopieringsproblem
description: I den här artikeln beskrivs möjliga lösningar på problem med att skapa säkerhetskopior.
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Säkerhetskopieringsproblem

I den här artikeln beskrivs möjliga lösningar på problem med att skapa säkerhetskopior.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.3.x
* Magento Open Source 2.3.x

## Säkerhetskopiering har inaktiverats {#backup-disabled}

Om Adobe Commerce säkerhetskopieringsfunktion inte startar eller visar följande meddelande måste du aktivera funktionen innan du säkerhetskopierar.

```bash
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

Ange följande CLI-kommando:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

Mer information om säkerhetskopiering finns i [Säkerhetskopiera och återställa filsystemet, mediet och databasen.](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-backup.html)

## Otillräckligt diskutrymme {#insufficient-disk-space-trouble-backup-space-}

Om säkerhetskopieringen misslyckas på grund av otillräckligt diskutrymme bör du vanligtvis frigöra diskutrymme genom att flytta vissa filer till en annan lagringsenhet eller enhet. Det kan dock finnas andra sätt att lösa problemet. Tips finns på någon av följande resurser:

* [8 Tips för att lösa problem med hårddisken i Linux &amp; Unix Systems som t.ex. disken full eller inte kan skriva till disken](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk)
* [serverdefault: df säger att disken är full, men inte ](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)
* [unix.stackexchange.com: Spåra var diskutrymmet har pågått i Linux?](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## Operativsystemfel {#operating-system-error-trouble-backup-os-}

Tyvärr kan vi inte rekommendera något specifikt på grund av den mängd olika fel som du kan råka ut för. Vi kan dock föreslå följande:

* Kontakta systemadministratören.
* Sök i allmänna forum som [Stapla Exchange](https://unix.stackexchange.com) eller [Stackspill](https://stackoverflow.com)
* Öppna ett [GitHub-problem](https://github.com/magento/magento2/issues) så försöker vi hjälpa till.

## Säkerhetskopieringen misslyckades {#backup-fails-trouble-backup-all-}

Om säkerhetskopieringen misslyckas eller om alla säkerhetskopieringstester misslyckas, är det möjligt att [Adobe Commerce-filsystemets ägare](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/file-sys-perms-over.html) inte har tillräcklig behörighet och ägarskap för Adobe Commerce-filsystemet. En annan användare kan till exempel äga filerna eller så är filerna skrivskyddade.

Var särskilt uppmärksam på filsystembehörigheter och ägarskap för katalogen och underkatalogerna `<magento_root>/var`. Mer information finns i [Ange behörigheter och ägarskap för filsystemet](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-system-perms.html).
