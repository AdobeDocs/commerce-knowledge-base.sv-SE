---
title: Produktstatusen är felaktig när den skapas programmatiskt
description: I den här artikeln finns en korrigering för när produktstatus är inaktiverad och produkter inte visas i butiken, eller tilldelas till fel butiksvyer när de skapas/uppdateras programmatiskt.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Produktstatusen är felaktig när den skapas programmatiskt

I den här artikeln finns en korrigering för när produktstatus är inaktiverad och produkter inte visas i butiken, eller tilldelas till fel butiksvyer när de skapas/uppdateras programmatiskt.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur 2.X.X
* Adobe Commerce lokal 2.X.X

## Problem

När katalogprodukterna skapas eller uppdateras via programkod från ett skript med Adobe Commerce-programmet startat, kan produkterna ha statusen Inaktiverat och/eller tilldelats fel butiksvy.

## Orsak

Problemet kan uppstå på grund av ACL-begränsningar för Adobe Commerce instansadministratörsroller. Om det är ett startprogram kommer det inte att finnas några initierade administratörssessioner med lämpliga ACL-inställningar. Det skulle göra att valideringar misslyckas i modulen `Magento_AdminGws`, som ansvarar för behörighetskontroll av sådana åtgärder.

## Lösning för felaktig produktstatus

Ange en dynamisk ID-inställning för `Magento\Framework\Authorization\PolicyInterface`, enligt beskrivningen i avsnittet [ ObjectManager>Programmatiska produktuppdateringar](https://developer.adobe.com/commerce/php/development/components/object-manager/) i utvecklardokumentationen.

## Relaterad läsning

* [Github: Det går inte att ändra produktstatus för produkt som skapats med productRepository](https://github.com/magento/magento2/issues/5664)
