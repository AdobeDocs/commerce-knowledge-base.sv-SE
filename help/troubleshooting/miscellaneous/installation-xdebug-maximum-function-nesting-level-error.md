---
title: Installations-xdebug för högsta funktionskkapslingsnivåfel
description: I den här artikeln finns en korrigering för xdebug maximum function nesting level error during installation.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# Installations-xdebug för högsta funktionskkapslingsnivåfel

I den här artikeln finns en korrigering för xdebug maximum function nesting level error during installation.

## Information

Under installationen av Adobe Commerce visas ett meddelande som liknar det här:

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

Vi rekommenderar starkt att du INTE ANVÄNDER `xdebug` i en produktionsmiljö!

## Lösning

Det finns ett känt problem med `xdebug` som kan påverka Adobe Commerce-installationer eller åtkomst till butiken eller Commerce Admin efter installationen.

Mer information finns i [Känt problem med xdebug](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md) i vår kunskapsbas för support.
