---
title: 'Distributionen misslyckades: Det går inte att använda MDVA-43395-korrigering'
description: Den här artikeln innehåller en lösning på problemet, där ett försök att använda MDVA-43395-korrigeringen leder till misslyckad distribution.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Molnhandlare behöver inte tillämpa MDVA-43395-korrigeringen separat om de har [magento/magento-cloud-patches 1.0.16](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016) installerad, som redan innehåller korrigeringen.

## Lösning

Du löser problemet genom att ta bort MDVA-43395- och MDVA-43443-korrigeringsfilerna från katalogen `m2-hotfixes` och sedan distribuera om.

Om du kunde tillämpa MDVA-43443-korrigeringen via katalogen `m2-hotfixes` måste du ändå ta bort den enligt ovan. I framtida versioner av Adobe Commerce finns dessa patchar redan i, så det kan leda till att distributionen misslyckas om du uppgraderar senare.

Kör kommandot `vendor/bin/magento-patches -n status |grep 43443` om du vill verifiera om korrigeringen har tillämpats.
Om det visar flera resultat som detta bör du ta bort MDVA-43443-korrigeringen från mappen `m2-hotfixes`:

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## Relaterad läsning

* [Använda en kompositörkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.
* [Molnkorrigeringar för Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016) i utvecklardokumentationen.
