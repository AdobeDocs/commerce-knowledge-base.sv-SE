---
title: Ändra öknings-ID för en databasenhet (order, faktura, kreditnota osv.) på en viss butik
description: I den här artikeln beskrivs hur du ändrar inkrement-ID för en enhet i en Adobe Commerce-databas (DB) (order, faktura, kreditnota osv.) på en viss Adobe Commerce-butik med SQL-satsen ALTER TABLE.
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Ändra öknings-ID för en databasenhet (order, faktura, kreditnota osv.) på en viss butik

I den här artikeln beskrivs hur du ändrar inkrement-ID för en enhet i en Adobe Commerce-databas (DB) (order, faktura, kreditnota osv.) på en viss Adobe Commerce-butik med `ALTER TABLE` SQL-sats.

## Berörda versioner

* Lokal Adobe Commerce: 2.x.x
* Adobe Commerce i molninfrastruktur: 2.x.x
* MySQL: any [version som stöds](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html#database)

## När behöver du ändra ID för ökning (fall)

Du kan behöva ändra ID:t för ökning för nya DB-entiteter i följande fall:

* Efter en återställning av en hård säkerhetskopiering på en Live-webbplats
* Vissa orderposter har gått förlorade, men deras ID används redan av betalningsgateways (som PayPal) för ditt aktuella Merchant-konto. Så är fallet, så upphör betalningsgatewayen att bearbeta nya order som har samma ID, vilket returnerar felet &quot;Duplicera faktura-ID&quot;

>[!NOTE]
>
>Du kan också åtgärda problemet med betalningsgateway för PayPal genom att tillåta flera betalningar per faktura-ID i PayPals Inställningar för betalningsmottagning. Se [PayPal-gateway avvisade begäran - dubblettfakturautleverans](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) i vår kunskapsbas för support.

## Krav på steg

1. Sök efter butiker och enheter som det nya tilläggs-ID:t ska ändras för.
1. [Anslut](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) till din MySQL-databas. För Adobe Commerce i molninfrastruktur måste du först [SSH i din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Kontrollera det aktuella auto\_increment-värdet för entitetssekvenstabellen med följande fråga:

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Exempel

Om du kontrollerar en automatisk ökning för en order i butiken med *ID=1* blir tabellnamnet:

```sql
'sequence_order_1'
```

Om värdet för `auto_increment` kolumnen är *1234*, nästa order som läggs i butiken med *ID=1* kommer att ha *ID \#100001234*.

### Relaterad dokumentation

* [Konfigurera en MySQL-fjärrdatabasanslutning](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) i vår dokumentation för utvecklare.

## Uppdatera enhet för att ändra öknings-ID

Uppdatera entiteten med följande fråga:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>Viktigt: Det nya stegvärdet måste vara större än det aktuella, inte mindre!

### Exempel

När följande fråga har körts:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

nästa order som läggs i butiken med *ID=1* kommer att ha *ID \#100002000*.

## Ytterligare rekommenderade steg i produktionsmiljön (Cloud)

Innan du kör `ALTER TABLE` fråga om Adobe Commerce produktionsmiljö i molninfrastrukturen rekommenderar vi att du utför följande steg:

* Testa hela proceduren för att ändra tilläggs-ID i mellanlagringsmiljön
* [Skapa](/help/how-to/general/create-database-dump-on-cloud.md) en DB-säkerhetskopia som återställer din produktionsdatabas om fel uppstår

## Relaterad dokumentation

* [Skapa databasdump i molnet](/help/how-to/general/create-database-dump-on-cloud.md) i vår kunskapsbas för support.
* [SSH i din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) i vår dokumentation för utvecklare.
