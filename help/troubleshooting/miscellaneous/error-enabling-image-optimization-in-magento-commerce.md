---
title: Fel vid aktivering av bildoptimering i Adobe Commerce
description: I den här artikeln finns en lösning på problemet när Snabbildsoptimering (IO) är inaktiverat som standard med ett meddelande om att kontakta Snabbt för att aktivera bildoptimering. (Fastly Cloud Image Optimizer är en tjänst för bildredigering och optimering i realtid som snabbar upp bildleveransen genom att leverera bandbreddseffektiva bilder.)
exl-id: 7b64c786-3c74-4642-b0d0-15b5648163a0
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Fel vid aktivering av bildoptimering i Adobe Commerce

I den här artikeln finns en lösning på problemet när Snabbildsoptimering (IO) är inaktiverat som standard med ett meddelande om att kontakta Snabbt för att aktivera bildoptimering. (Fastly Cloud Image Optimizer är en tjänst för bildredigering och optimering i realtid som snabbar upp bildleveransen genom att leverera bandbreddseffektiva bilder.)

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x

## Problem

På sidan Snabbkonfiguration, bredvid IO-kodfragmentet Fast, ser du läget Aktuell: \_disabled \_med följande meddelande under: Kontakta din säljare eller skicka ett e-postmeddelande till `support@fastly.com` för att begära aktivering av bildoptimering för tjänsten Snabbt.

## Orsak

Webbplatsen kanske inte är publicerad än. Det finns processer för att förhandsladda webbplatsen när den publiceras i snabbdatabasen.

## Lösning

Skapa en [Supportbiljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och begär optimering av bilder.
