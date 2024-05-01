---
title: 404 det gick inte att hitta något fel vid åtkomst till guiden för webbkonfiguration via administratörspanelen
description: I den här artikeln finns en lösning för när du får ett felmeddelande om att 404 inte hittades när du försöker få åtkomst till webbinstallationsguiden via administratörspanelen.
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

Se [Installera, hantera och uppgradera tillägg](https://devdocs.magento.com/cloud/howtos/install-components.html) i vår utvecklardokumentation om du vill ha information om hur du utför uppdateringar eller installerar externa moduler för Adobe Commerce i vår molninfrastruktur.
Se [Snabbstart](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) i vår utvecklardokumentation om du vill ha information om hur du utför uppdateringar eller installerar externa moduler för Adobe Commerce lokalt.

## Relaterad läsning

* Se [Installera ett tillägg](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension) i vår dokumentation för utvecklare.
