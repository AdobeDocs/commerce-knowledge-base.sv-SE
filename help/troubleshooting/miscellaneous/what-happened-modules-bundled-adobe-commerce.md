---
title: Moduler saknas i Adobe Commerce 2.4.4
description: Den här artikeln innehåller en lösning på problemet när moduler som ingår i tidigare versioner av Adobe Commerce inte finns med i 2.4.4.
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Moduler saknas i Adobe Commerce 2.4.4

Den här artikeln innehåller en lösning för när moduler som ingår i tidigare versioner av Adobe Commerce inte finns med i 2.4.4.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) alla  [versionerna](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Du kan inte installera en tredjepartsmodul eller har upptäckt att vissa av de kärnpaket som ingår inte finns när du uppgraderar till Adobe Commerce 2.4.4. Detta bör endast bero på installation av en tredjepartsmodul som kräver ett av de programtillägg som tagits bort från Adobe Commerce 2.4.4 eller om projektet använder vissa funktioner i en av de borttagna modulerna.

* Scenario 1: Projektet har använt en av de viktigaste funktionerna i den paketerade modulen. Den använda paketmodulen ingår inte i Adobe Commerce 2.4.4. När du har uppgraderat till Adobe Commerce 2.4.4 är du medveten om att modulen och dess tillhandahållna funktioner saknas.

* Scenario 2: Du har en modul installerad i ditt aktuella projekt som är beroende av en av de borttagna paketerade modulerna.

Detta är förväntat eftersom leverantörspaketerade tillägg har tagits bort från kodbasen för Adobe Commerce 2.4.4.

## Lösning

Installera/köp de officiella tilläggen separat. Dessa finns på [Commerce Marketplace](https://marketplace.magento.com/extensions.html).

## Relaterad läsning

[Leverantörsprogramtillägg](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?#vendor-bundled-extensions) i Adobe Commerce Documentation > Release Information > Versionsinformation för Adobe Commerce 2.4.4.
