---
title: Vanliga frågor om aktivering av ursprungsinsvepning för [!DNL Fastly]
description: Vanliga frågor och svar behandlar frågor om  [!DNL Fastly] ursprungsinsvepning i Adobe Commerce (som har implementerats fullt ut 2021).
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Vanliga frågor om aktivering av ursprungsinsvepning för [!DNL Fastly]

Vanliga frågor och svar behandlar vanliga frågor om [!DNL Fastly] ursprungsinsvepning i Adobe Commerce (som har implementerats fullt ut 2021).

## Vad är [!DNL Fastly]-ursprung som insveper?

Insvepning av ursprung är en säkerhetsfunktion som gör att Adobe Commerce i molninfrastrukturen kan blockera all [!DNL non-Fastly]-trafik (för att förhindra DDoS-attacker, gå till molninfrastrukturen (ursprung).

## Vilka är fördelarna med ursprungsinsvepning?

Insvepning av startpunkt är utformat för att förhindra att trafik kringgår [!DNL Fastly Web Application Firewall] (WAF) och dirigerar den via det strikt definierade flödet för **[!DNL Fastly]** > **belastningsutjämnare** > **instanser**. Med den här implementeringen garanteras all trafik att passera både [!DNL Fastly] WAF och den interna WAF som är inbyggd i belastningsutjämnaren.

## Varför sker det här insvepningen?

Den här funktionen skapades ursprungligen för att gynna Adobe Commerce på molninfrastrukturen.

## Behöver jag begära aktivering av ursprungsinsvepning för mitt projekt?

Nej. Den här funktionen bör redan ha implementerats för alla molnprojekt och alla projekt som har etablerats sedan 2021 skulle ha aktiverats som standard.

## Ändrar ursprungsinsvepning den utgående IP-adressen?

Nej, det gör det inte.

## Påverkar ursprungsinsvepning REST API?

[!DNL Fastly] cache-lagrar inte API-anrop, så klienten bör vara okej med ändringen. Insvepning av enbart ursprung blockerar begäranden som går direkt till ursprunget, som:

* Produktion

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

* Mellanlagring

```php
mcstaging2.mywebsite.com.c.abcdefghijkl.dev.ent.magento.cloud
```

* StagingX

```php
mcstagingX.mywebsite.com.c.abcdefghijkl.X.dev.ent.magento.cloud
```

I det här exemplet kan klienten fortfarande nå API:t om de ändrar URL:en till ``mywebsite.com``:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Kommer förändringen att påverka driftsättning och driftstopp?

Nej, den här ändringen **NOT** påverkar distributionen och driftstoppen.

## Om projektet har flera mellanlagringsmiljöer, kommer ursprungsinsvepning att användas i alla mellanlagringsmiljöer?

Ja, om projektet har flera mellanlagringsmiljöer används ändringen i alla mellanlagringsmiljöer.
