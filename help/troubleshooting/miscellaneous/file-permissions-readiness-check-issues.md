---
title: Problem med beredskapskontroll av filbehörigheter
description: '"Den här artikeln innehåller en korrigering för problem med kontroll av filbehörigheter. Kataloger i Adobe Commerce filsystem måste vara skrivbara av webbserveranvändaren och Adobe Commerce filsystemsägare, om tillämpligt. Ett fel som liknar följande visas i Web Setup Wizard om behörigheterna inte är korrekt angivna:'''
exl-id: 252e6e7d-5269-44ce-b3ce-6fc2ea6a1c5c
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Problem med beredskapskontroll av filbehörigheter

I den här artikeln finns en korrigering för problem med kontroll av filbehörigheter. Kataloger i Adobe Commerce filsystem måste vara skrivbara av webbserveranvändaren och Adobe Commerce filsystemsägare, om tillämpligt. Ett fel som liknar följande visas i Web Setup Wizard om behörigheterna inte är korrekt angivna:

![install_rc_file-perms.png](assets/install_rc_file-perms.png)

Hur du löser problemet beror på om du har en eller två användare:

* *En användare* innebär att du loggar in på Adobe Commerce-servern som samma användare som kör webbservern. Den här typen av konfiguration är vanlig i delade värdmiljöer.
* *Två användare* betyder att du *inte* loggar in som, eller växlar till, webbserveranvändaren. Du loggar vanligtvis in som en användare och kör webbservern som en annan användare. Detta är typiskt för privata värdtjänster eller om du har en egen server.

## Enanvändarupplösning

Om du har kommandoradsåtkomst anger du följande kommando under förutsättning att Adobe Commerce är installerat i `/var/www/html/magento2`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+w {} + && chmod u+x bin/magento
```

Om du inte har kommandoradsåtkomst kan du ange behörigheter med hjälp av en FTP-klient eller ett filhanteringsprogram från din värdleverantör.

## Upplösning med två användare

Om du vill ange alla kommandon på en rad anger du följande under förutsättning att Adobe Commerce är installerat i `/var/www/html/magento2` och webbservergruppens namn är `apache`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Om filsystembehörigheterna inte har angetts korrekt och inte kan ändras av Adobe Commerce filsystemägare, kan du ange kommandot som en användare med `root` behörighet:

```bash
$ cd /var/www/html/magento2 && sudo find var vendor
  pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find
  var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + &&
  sudo chown -R :apache . && sudo chmod u+x bin/magento
```
