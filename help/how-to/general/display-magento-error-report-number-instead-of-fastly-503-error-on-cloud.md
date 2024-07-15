---
title: Visa Adobe Commerce-felrapportnummer i stället för Fastly 503-fel
description: Som standard döljs alla Adobe Commerce-fel automatiskt bakom felet **503 Service Unavailable**. Om du vill visa rapportnumret för Adobe Commerce fellogg (för att kunna hitta det i loggar och se felinformationen) öppnar du webbplatsen utan att använda dessa steg:"
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Visa Adobe Commerce-felrapportnummer i stället för Fastly 503-fel

Som standard döljer Fastly alla Adobe Commerce-fel bakom felet **503-tjänsten är inte tillgänglig** . Om du vill visa rapportnumret för Adobe Commerce fellogg (för att kunna hitta det i loggar och se felinformationen) öppnar du webbplatsen utan att använda dessa steg:

1. Lägg till programmets domän och IP-adress i värdfilen på den lokala datorn.
1. Rensa webbläsarens cache och cookies (eller växla till inkognito-läge).
1. Öppna butikens webbplats igen och se Adobe Commerce-felet.

När du ser det äkta Adobe Commerce-felet och felrapportnumret kan du få information i felrapportfilen genom att följa dessa steg:

1. SSH till den drabbade miljön. Se [SSH till en miljö](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh) i utvecklardokumentationen.
1. Leta reda på filen `./var/report/{error_number}`.

## Lägg till programdomän och IP-adress till din värdfil: detaljerade steg

1. Kontrollera lagringsplatsens server-IP genom att köra kommandot `nslookup` på kommandoraden på den lokala datorn:
   * Användare av Pro-arkitektur (miljö för staging och produktion):

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * Användare av startarkitektur (alla miljöer); användare av Pro-arkitektur (integreringsmiljö):

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. Lägg till din lagringsdomän och IP-adress för programserver i värdfilen på den lokala datorn i följande format:

```
{server_IP} {store_domain}
```
