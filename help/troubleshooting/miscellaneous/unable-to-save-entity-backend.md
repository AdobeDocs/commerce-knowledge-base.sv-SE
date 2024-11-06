---
title: Det går inte att spara enheten Adobe Commerce backend
description: Den här artikeln innehåller en lösning för när du inte kan spara en enhet i Adobe Commerce serverdel. Om du till exempel inte kan redigera och spara en viss kundvagnsregel.
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Det går inte att spara enheten Adobe Commerce backend

Den här artikeln innehåller en lösning för när du inte kan spara en enhet i Adobe Commerce serverdel. Om du till exempel inte kan redigera och spara en viss `cart_price`-regel.

## Berörda produkter och versioner

Problemet kan påverka alla Adobe Commerce-versioner som har konfigurerat maximal sessionsstorlek. Detta lades till från och med Magento Open Source 2.3.7-p1 och Adobe commerce (alla distributionsmetoder) 2.4.3.


## Problem

När du försöker konfigurera om din butik läses sidan in igen och ändringarna sparas inte. Ett meddelande visas i `var/log/system.log`:

*[2021-11-27 00:30:52] rapport.VARNING! Sessionsstorleken 418056 överskrider den tillåtna sessionsstorleken på 256000. [][]*

<u>Steg som ska återskapas</u>:

Ett exempel på lagringskonfigurationen sparas inte:

1. Välj en regel i Adobe Commerce Store i Produktion > **Marknadsföring** > **Kundprisregler**.
1. Välj en regel och ange den till *Inaktiv* och spara ändringen.

<u>Förväntat resultat</u>:

Regeln är inställd på inaktiv.

<u>Faktiskt resultat</u>:

* Sidan laddas om utan något meddelande.
* Regeln är fortfarande aktiv.

## Orsak

Det här problemet har att göra med nya funktioner som nyligen introducerades och som har påverkat den maximala sessionsstorleken. Se [Sessionshantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management) i utvecklardokumentationen.

## Lösning

Öka värdet för Maximal sessionsstorlek i (**Lagrar** > **Konfiguration** > **Avancerat** > **System** > **Säkerhet** > Maximal sessionsstorlek).

## Relaterad läsning

* [Marknadsföringsmeny](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/marketing-menu) i vår användarhandbok.
