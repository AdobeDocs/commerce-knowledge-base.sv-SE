---
title: Kan jag installera program från tredje part i min molninstans?
description: Nej. Det är inte tillåtet att installera program från tredje part (som WordPress eller Drupal) på Adobe Commerce på molninfrastrukturservrar. Du måste ha sådana program på externa servrar.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Kan jag installera program från tredje part i min molninstans?

Nej. Det är inte tillåtet att installera program från tredje part (som WordPress eller Drupal) på Adobe Commerce på molninfrastrukturservrar. Du måste ha sådana program på externa servrar.

## Orsaker

### Villkor för serviceavtal

Adobe Commerce on cloud Infrastructure Edition [Terms of Service Agreement](https://magento.com/legal/terms/cloud-terms) innehåller följande i artikel 18:

> Kunden godkänner att Adobe Commerce och tjänsten inte kommer att användas som värd för andra tredjepartsprogram som inte är direkt beroende av Programvaran.

Adobe är en molnlösning och har fullt ansvar för serversäkerheten. För att garantera hög säkerhet tillåter vi endast att Adobe Commerce-programmet finns på den dedikerade molnservern.

### PCI-kompatibilitet

Som PCI-certifierad nivå 1-lösningsleverantör måste Adobe Commerce i molninfrastruktur följa PCI Data Security Standard och se till att:

>... utveckla och underhålla säkra system och tillämpningar
> ([Adobe inflygning till PCI-kompatibilitet](https://magento.com/pci-compliance) Krav 6, behåll ett Vulnerability Management Program)

Eftersom Adobe inte kan garantera PCI-kompatibiliteten för tredjepartsprogram är det inte tillåtet att installera sådana program på molnservrar.

## Tips: Använd Commerce Marketplace-tillägg för bättre integrering

För att förbättra integreringen av ditt Adobe Commerce i molninfrastruktursprogram med tredjepartslösningar som finns på externa servrar rekommenderar vi att du använder [Commerce Marketplace](https://marketplace.magento.com)-tillägg som passar ditt syfte.
