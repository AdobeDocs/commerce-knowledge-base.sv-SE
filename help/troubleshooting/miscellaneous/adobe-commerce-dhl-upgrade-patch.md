---
title: Använd en patch för att fortsätta erbjuda DHL som fraktfirma
description: I den här artikeln finns en patch som gör det möjligt för handlare som använder Adobe Commerce 2.4.4 och tidigare att fortsätta erbjuda DHL-leverans efter att DHL-schema 6.0 tagits bort i slutet av juli-september 2022.
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Använd en patch för att fortsätta erbjuda DHL som fraktfirma


## Berörda produkter och versioner

* Adobe Commerce 2.4.4 och tidigare, alla distributionsmetoder.

## Problem

DHL introducerar en 6.2-schemaversion och ersätter version 6.0 i slutet av juli-september 2022. Adobe Commerce 2.4.4 och tidigare DHL-integration stöder endast version 6.0.

## Lösning

Adobe Commerce 2.4.5, som planeras släppas i augusti 2022, kommer att innehålla den uppgraderade integrationen med DHL med version 6.2-schemat. Till dess att den nya versionen släpps (eller om du inte uppgraderar) rekommenderar vi att du använder AC-3022-korrigeringen och implementerar DHL-schemastöd version 6.2 för att fortsätta erbjuda DHL-leveranser i din butik efter borttagningen.

## Lappa

Patch-ID:t är AC-3022 som finns i Quality Patches Tool version 1.1.16.
Mer information om hur du använder QPT och installerar korrigeringsfiler finns i artikeln [Quality Patches Tool (QPT) > Usage](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i utvecklardokumentationen.

Patchen gäller för följande Adobe Commerce-versioner:

* 2.4.0 - 2.4.4-p1
* 2.3.7

## Relaterad läsning

* [Transportföretag > DHL](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl) i användarhandboken
* [Leveransmetoder](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/delivery-methods) i användarhandboken
