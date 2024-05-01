---
title: Behöver jag Fast för en Headless Adobe Commerce-sajt?
description: Behöver jag Fast för en Headless Adobe Commerce-sajt?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Behöver jag Fast för en Headless Adobe Commerce-sajt?

>[!NOTE]
>
>Alla kunder måste använda Fast för sin produktion och sina staging-miljöer. Fast är ett CDN-nätverk (Content Delivery Network) som tillhandahåller helsidescachning, bildoptimering och säkerhetstjänster (DDoS och WAF) som en del av Adobe Commerce i molninfrastrukturprojekt. Detta är kärnkomponenter i Adobe Commerce-lösningen, vilket ger högre prestanda och säkerhet. Dessa funktioner ingår i Adobe PCI-efterlevnad. Du måste konfigurera dessa snabbfunktioner i dina miljö Starter Master, Staging, Pro Staging och Production. Om du använder Adobe Commerce i en headlessdistribution måste all API-trafik från det offentliga Internet passera snabbt och vi rekommenderar att du använder Fast för att cachelagra GraphQL-svar. Se [GraphQL Developer Guide > Caching with Fast](https://devdocs.magento.com/guides/v2.3/graphql/caching.html#caching-with-fastly) i vår dokumentation för utvecklare.

## **Fråga**

Jag utvecklar en headless implementation av Adobe Commerce. Måste jag fortfarande använda Fastly som CDN-tjänst för den?

## **Svar**

Nej, det gör du inte. I den här situationen kan du hoppa över att använda Fastt - åtminstone i början av utvecklingen.

Den enda situation som du kanske inte vill aktivera är en headless-distribution.
Se [Cloud för Adobe Commerce > Snabbt](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html) i vår dokumentation för utvecklare.

Men du behöver antagligen Fast för att kunna använda SSL-certifikatet.

Alla kunder som har en molninfrastruktur får ett delat SSL-certifikat från Fastly som en del av molnprenumerationsplanen. Att lägga till ett eget SSL-certifikat till Fastly är ett separat och relativt dyrt betalningsalternativ. Därför rekommenderar vi starkt att du aktiverar Snabbt och åtminstone testar det i mellanlagrings- och produktionsmiljöer innan du publicerar - även för den headless Adobe Commerce-webbplatsen.

## Mer information

* [Headless Websites: What&#39;s the Big Deal with Decouattached Architecture?](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture) av [Josh Koenig](https://pantheon.io/team/josh-koenig).
* [Snabbt](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html) i vår dokumentation för utvecklare.
