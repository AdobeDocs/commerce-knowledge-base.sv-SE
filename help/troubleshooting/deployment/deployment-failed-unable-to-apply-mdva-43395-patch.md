---
title: 'Distributionen misslyckades: det går inte att använda MDVA-43395-korrigering'
description: Den här artikeln innehåller en lösning på problemet, där ett försök att använda MDVA-43395-korrigeringen leder till misslyckad distribution.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Distributionen misslyckades: Det går inte att använda MDVA-43395-korrigering

Den här artikeln innehåller en lösning på problemet, där ett försök att använda MDVA-43395-korrigeringen leder till misslyckad distribution.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur (alla versioner)

## Problem

Du kan inte använda MDVA-43395-korrigeringen.

## Orsak

Molnhandlare behöver inte tillämpa MDVA-43395-korrigeringen separat om de har [magento/magento-cloud-patches 1.0.16](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) som redan innehåller korrigeringen.

## Lösning

Du löser problemet genom att ta bort MDVA-43395- och MDVA-43443-korrigeringsfilerna från `m2-hotfixes` katalog och omdistribuera.

Om du kunde applicera MDVA-43443-korrigeringen via `m2-hotfixes` måste du ändå ta bort den enligt ovan. I framtida versioner av Adobe Commerce finns dessa patchar redan i, så det kan leda till att distributionen misslyckas om du uppgraderar senare.

För att bekräfta om patchen har applicerats, kör du `vendor/bin/magento-patches -n status |grep 43443` -kommando.
Om den visar flera resultat som detta bör du ta bort MDVA-43443-korrigeringen från `m2-hotfixes` mapp:

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## Relaterad läsning

* [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.
* [Cloud Patches for Commerce](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) i vår dokumentation för utvecklare.
