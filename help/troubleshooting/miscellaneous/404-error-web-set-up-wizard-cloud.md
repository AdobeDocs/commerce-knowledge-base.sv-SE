---
title: 404 det gick inte att hitta något fel vid åtkomst till guiden för webbkonfiguration via administratörspanelen
description: I den här artikeln finns en lösning för när du får ett felmeddelande om att 404 inte hittades när du försöker få åtkomst till webbinstallationsguiden via administratörspanelen.
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 404 det gick inte att hitta något fel vid åtkomst till guiden för webbkonfiguration via administratörspanelen

I den här artikeln finns en lösning för när du får ett felmeddelande om att 404 inte hittades när du försöker få åtkomst till webbinstallationsguiden via administratörspanelen.

## Berörda produkter och versioner

* Webbinstallationsguiden har tagits bort i Adobe Commerce (alla distributionsmetoder) 2.3.6 och tagits bort i 2.4.0.

## Problem

När du installerar ett tillägg med hjälp av webbinstallationsguiden visas en 404-sida.

<u>Steg som ska återskapas</u>:

Merchant klickar på webbinstallationsguiden för att installera en ny modul/integrering.

<u>Förväntat resultat</u>:

Installationer av modul/integrering.

<u>Faktiskt resultat</u>:

Ett 404-fel visas.

## Orsak

Webbinstallationsguiden har inaktiverats för alla Adobe Commerce i molninfrastrukturinstanser - det går inte att aktivera den. Tillägg måste installeras via disposition.

## Lösning

Den här funktionen är inaktiverad på Adobe Commerce i molninfrastruktur.

Se [Installera, hantera och uppgradera tillägg](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure-store/extensions) i utvecklardokumentationen för mer information om hur du utför uppdateringar eller installerar externa moduler för Adobe Commerce i vår molninfrastruktur.
Se [Snabbstartsinstallation](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/composer) i utvecklardokumentationen för mer information om hur du utför uppdateringar eller installerar externa moduler för Adobe Commerce lokalt.

## Relaterad läsning

* Se [Installera ett tillägg](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure-store/extensions#install-an-extension) i utvecklardokumentationen.
