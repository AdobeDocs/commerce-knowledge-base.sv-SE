---
title: EU-kunder kan inte slutföra betalningar
description: I den här artikeln finns en fix om problemet med att kunder från EU inte kan slutföra betalningar.
exl-id: 8309d96b-47a3-4d27-b538-e6e3bcdfb7d4
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# EU-kunder kan inte slutföra betalningar

I den här artikeln finns en fix om problemet med att kunder från EU inte kan slutföra betalningar.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner
* Adobe Commerce lokal 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problem

Kunder från EU klagar på att deras kreditkortstransaktioner avvisas.

## Orsak

Europeiska unionen reviderade en förordning som kallas betaltjänstdirektiv (PSD) med den uppdaterade versionen [PSD2](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015L2366&amp;from=EN). Detta är ett EU-direktiv som har införts för att reglera betaltjänster och betaltjänstleverantörer i hela EU och EES. Stark kundautentisering (SCA) är ett krav i PSD2 för att öka säkerheten och autentiseringen av betalningsdata. Om dina betalningslösningar inte uppfyller kraven i direktivet kan det leda till att kunderna inte kan slutföra betalningar. Mer information finns i det [relaterade Adobe Commerce DevBlog-inlägget](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460).

## Lösning

Följ rekommendationerna från avsnittet [Adobe Commerce Payment Provider Recommendations i DevBlog](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460#recommendations).
