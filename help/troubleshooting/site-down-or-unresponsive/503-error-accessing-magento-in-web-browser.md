---
title: 503-fel vid åtkomst till Adobe Commerce i webbläsaren
description: I den här artikeln finns en möjlig lösning på problemet där du får ett 503-fel när du försöker få åtkomst till Adobe Commerce storefront och/eller Admin.
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 503-fel vid åtkomst till Adobe Commerce i webbläsaren

I den här artikeln finns en möjlig lösning på problemet där du får ett 503-fel när du försöker få åtkomst till Adobe Commerce storefront och/eller Admin.

## Berörda produkter och versioner

Adobe Commerce 2.3.x

## Problem {#symptoms}

<u>Steg som ska återskapas</u>

(Krav: kontrollera att arkivet inte är i [underhållsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cli/set-mode#config-mode-show).)

Navigera till Commerce Admin eller Store i en webbläsare.

<u>Förväntat resultat</u>

Sidan läses in.

<u>Faktiskt resultat</u>

HTTP 503-felet (tjänsten är inte tillgänglig) visas. Apache `error.log` innehåller följande meddelande:

*Ogiltigt kommando, Order, kanske felstavat eller definierat av en modul som inte ingår i serverkonfigurationen.*

## Orsak {#details}

Kompatibilitetsmodulen `mod_access_compat` för Apache 2.4 är inaktiverad, vilket gör att Adobe Commerce URL-skrivningar inte fungerar som de ska.

## Lösning {#suggested-solution}

Aktivera Apache-modulen `mod_access_compat` och starta om Apache genom att köra följande som en användare med behörighet för root:

```bash
a2enmod access_compat
service <name> restart
```

I CentOS

```bash
<name>
```

är

```bash
httpd
```

. På Ubuntu

```bash
<name>
```

är

```bash
apache2
```

.

## Relaterad läsning {#additional-resources}

* [Apache-dokumentation om mod\_access\_compat](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [Apache-dokumentation om mod\_authz\_host](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [Beställa, tillåt, neka från den slutgiltiga Apache-guiden](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
