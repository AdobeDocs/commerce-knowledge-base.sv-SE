---
title: Behörighetsproblem för var-/exportmappen för Adobe Commerce i molnet
description: I den här artikeln finns en lösning på ett problem där du inte kan exportera produktdata på grund av ett filbehörighetsproblem på servern i mappen "var/export/email". Symtomen är bland annat att produkt- och katalogexport inte är tillgänglig i användargränssnittet, men visas när SSH används.
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Behörighetsproblem för var-/exportmappen för Adobe Commerce i molnet

Den här artikeln innehåller en lösning på ett problem där du inte kan exportera produktdata på grund av ett filbehörighetsproblem på servern i mappen `var/export/email`. Symtomen är bland annat att produkt- och katalogexport inte är tillgänglig i användargränssnittet, men visas när SSH används.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Problem

Du kan inte exportera filer i mappen `var/export/email` eller `var/export/archive`.
Distributionen misslyckades på grund av behörigheter på `var/export/email` eller `var/export/email/archive` eftersom arkivmappen skapas via e-post och om jag bara gör export/e-post ibland finns det fortfarande ett problem) förutom att något läggs till för kontot för undermappen `var/export/email/archive`.

<u>Steg som ska återskapas</u>:

Gå till **System** > *Dataöverföring* > **Exportera** i Admin.
Markera de CSV-filer som ska sparas i mappen `var/export/`.

<u>Förväntat resultat</u>:

CSV-filer är synliga och kan exporteras.

<u>Faktiskt resultat</u>:

CSV-filer är inte synliga. Du ser också ett meddelande om nekad behörighet: *RecursiveDirectoryIterator::__construct(/app/project id>/var/export/email): failed open dir: Permission deny*

Du får samma meddelande för alla exporttyper: Avancerade priser, Kundekonomi, Kundens huvudfil och Kundadresser.

## Orsak

Detta orsakas av en mapp som skapats inuti `/var` som har felaktiga behörigheter: `d-wxrwsr-T`. T-klisterbiten innebär att användarna bara kan ta bort de filer de äger, men den saknade körbara filen innebär att de inte kan skapa filer i katalogen.

Detta märks ofta när systemet skapar en mapp med namnet `export` som innehåller en mapp med namnet `email` som innehåller en mapp med namnet `archive`.

Om du vill kontrollera om katalogen har dessa felkonfigurerade behörigheter kör du följande kommando i CLI/Terminal:

`ls -ld var/export/`

Om behörigheterna är felkonfigurerade blir utdata:

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## Lösning

Du kan åtgärda detta genom att uppdatera behörigheterna för mapparna till 777 och sedan alla filer rekursivt genom att köra följande kommandon:

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## Relaterad läsning

* [Exportera](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/data-transfer/data-export) i vår användarhandbok.
