---
title: Basprisändringen påverkar det delade katalogpriset
description: 'Den här artikeln besvarar frågan: Om en produkt i en delad katalog har ett anpassat pris och produktens baspris ändras (till exempel efter en schemalagd uppdatering), vilket pris gäller i den delade katalogen?'
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Basprisändringen påverkar det delade katalogpriset

Den här artikeln besvarar frågan: Om en produkt i en delad katalog har ett anpassat pris och produktens baspris ändras (till exempel efter en schemalagd uppdatering), vilket pris gäller i den delade katalogen?

## Med anpassat pris satt till Procent ändras även priset för delade kataloger

Om det anpassade priset för en produkt i en delad katalog har angetts till Procentandel, uppdateras produktens delade katalogpris implicit efter att baspriset har ändrats.

När baspriset uppdateras (via en normal eller schemalagd uppdatering) ändras alltså även priset för den delade katalogen efter att procentrabatten tillämpats.

## Om det anpassade priset är fast ändras inte priset för den delade katalogen

Om det anpassade priset för en produkt i en delad katalog har angetts till Fast, ändras aldrig priset i den delade katalogen - oavsett hur vi uppdaterar baspriset (via schemalagd uppdatering, Adobe Commerce Admin, API eller import).

## I Storefront visas alltid lägsta tillgängliga pris

Om produktens baspris ändras och blir mindre än det motsvarande delade katalogpriset visas baspriset som det lägsta tillgängliga priset i systemet.

## Relaterad läsning

[Ange priser och struktur för en delad katalog](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/define/catalog-shared-pricing-structure.html?lang=sv-SE) i användarhandboken.
