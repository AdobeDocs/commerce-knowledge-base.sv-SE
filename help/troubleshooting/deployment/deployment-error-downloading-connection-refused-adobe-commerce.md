---
title: 'Distributionsfel: *fel 7 vid hämtning ... port 443: Anslutningen nekades*'
description: '"Den här artikeln innehåller en lösning för distributionsfelet: *"fel 7 vid hämtning ... port 443: Anslutningen nekades"*."'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Distributionsfel: *fel 7 vid hämtning ... port 443: Anslutningen nekades*

Den här artikeln innehåller en korrigering för problemet när distributionen misslyckas med följande felmeddelande:

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## Berörda versioner

Adobe Commerce i molninfrastruktur, [alla versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Distributionen misslyckas med ett **krullningsfel 7**-meddelande.

<u>Steg som ska återskapas</u>:

Utlös en distribution.

<u>Förväntat beteende</u>:

Distributionen har slutförts.

<u>Faktiskt beteende</u>:

Distributionen misslyckas och följande fel: *krullningsfel 7 vid hämtning ... port 443: Anslutningen nekades* visas i distributionsloggen.

## Orsak

Detta kan bero på att cacheanslutningen förloras till repon.

## Lösning

Be en superanvändare i projektet att köra det här kommandot:

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

Om du vill kontrollera vem som har en superanvändare i projektet kan du läsa [Visa en användares projektroll](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) i Commerce on Cloud Infrastructure Guide.

## Rekommenderad läsning

* [Adobe Commerce felsökare för distribution](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html).
* [Det gick inte att komma åt Adobe Commerce i molnet: 403 Otillåten eller 404 Det gick inte att hitta felet vid distributionen](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [Distributionen misslyckas med felet&quot;Det gick inte att skapa projektet: Byggkopplingen misslyckades med statuskoden 1&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
