---
title: Administratörslösenord sparade som oformaterad text i åtgärdsloggen
description: I den här artikeln finns en fix som du kan använda när en Commerce-administratör skapar en ny användare med administratörsbehörighet och lösenordet sparas som oformaterad text i databastabellen "magento_log_event_changes".
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Administratörslösenord sparade som oformaterad text i åtgärdsloggen

Den här artikeln innehåller en korrigering för när en Commerce-administratör skapar en ny användare med administratörsbehörighet och lösenordet sparas som oformaterad text i databastabellen `magento_logging_event_changes`.

Installera säkerhetsuppdateringen för Adobe Commerce 2.0.16 och 2.1.9 för att åtgärda det här säkerhetsproblemet. När säkerhetsuppdateringen har tillämpats krypteras lösenorden och visas inte som oformaterad text.

## Berörda versioner {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce lokal 2.X.X
* Adobe Commerce i molninfrastruktur 2.X.X

## Problem {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

När en befintlig Commerce-administratör skapar en ny användare med administratörsbehörighet via **System** > **Behörigheter** > **Alla användare** > **Lägg till ny användare** sparas lösenordet (anges som en bekräftelse) som oformaterad text i databastabellen `magento_logging_event_changes`.

### Steg som ska återskapas: {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. Logga in som administratör och skapa en ny användare genom att navigera till den här sökvägen: **System** > Behörigheter > **Alla användare**.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. Klicka sedan på sidan **Lägg till ny användare**. Ange den aktuella administratörens lösenord när du uppmanas till det.
1. Gå till sidan **System** > **Åtgärdslogg** > **Rapport** och hitta den senaste loggposten.
1. Du kan se det aktuella lösenordet, varken krypterat eller hashas.

## Lösning {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

Problemet åtgärdas genom att [Adobe Commerce 2.0.16 och 2.1.9-säkerhetsuppdateringen](https://magento.com/security/patches/magento-2016-and-219-security-update) installeras.

När säkerhetsuppdateringen har installerats krypteras lösenordet och visas inte i oformaterad text i tabellen `magento_logging_event_changes`.

## Mer information {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

[Adobe Commerce 2.0.16 och 2.1.9 Security Update page](https://magento.com/security/patches/magento-2016-and-219-security-update) i vårt säkerhetscenter.

[Uppgradera Adobe Commerce-programmet och komponenterna](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) i utvecklardokumentationen.
