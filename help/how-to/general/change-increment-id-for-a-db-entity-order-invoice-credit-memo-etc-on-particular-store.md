---
title: Ändra öknings-ID för en databasenhet (order, faktura, kreditnota osv.) på en viss butik
description: I den här artikeln beskrivs hur du ändrar tilläggs-ID för en Adobe Commerce-databasentitet (order, faktura, kreditnota osv.) på en viss Adobe Commerce-butik med SQL-satsen "ALTER TABLE".
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Ändra öknings-ID för en databasenhet (order, faktura, kreditnota osv.) på en viss butik

I den här artikeln beskrivs hur du ändrar tilläggs-ID för en Adobe Commerce-databasentitet (order, faktura, kreditnota osv.) på en viss Adobe Commerce-butik med hjälp av SQL-satsen `ALTER TABLE`.

## Berörda versioner

* Lokal Adobe Commerce: 2.x.x
* Adobe Commerce i molninfrastruktur: 2.x.x
* MySQL: any [supported version](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/system-requirements)

## När behöver du ändra ID för ökning (fall)

Du kan behöva ändra ID:t för ökning för nya DB-entiteter i följande fall:

* Efter en återställning av en hård säkerhetskopiering på en Live-webbplats
* Vissa orderposter har gått förlorade, men deras ID används redan av betalningsgateways (som PayPal) för ditt aktuella Merchant-konto. Så är fallet, så upphör betalningsgatewayen att bearbeta nya order som har samma ID, vilket returnerar felet &quot;Duplicera faktura-ID&quot;

>[!NOTE]
>
>Du kan också åtgärda problemet med betalningsgateway för PayPal genom att tillåta flera betalningar per faktura-ID i PayPals Inställningar för betalningsmottagning. Se [PayPal-gatewayen avvisade begäran - dubblettfakturaproblem](https://experienceleague.adobe.com/sv/docs/experience-cloud-kcs/kbarticles/ka-26838) i vår kunskapsbas för support.

## Krav på steg

1. Sök efter butiker och enheter som det nya tilläggs-ID:t ska ändras för.
1. [Anslut](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote) till din MySQL-databas. För Adobe Commerce i molninfrastruktur måste du först [SSH till din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=sv-SE).
1. Kontrollera det aktuella auto\_increment-värdet för entitetssekvenstabellen med följande fråga:

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Exempel

Om du kontrollerar en automatisk ökning för en order i butiken med *ID=1* blir tabellnamnet:

```sql
'sequence_order_1'
```

Om värdet för kolumnen `auto_increment` är *1234* får nästa ordning som placeras i butiken med *ID=1* *ID \#100001234*.

### Relaterad dokumentation

* [Konfigurera en MySQL-fjärrdatabasanslutning](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote) i utvecklardokumentationen.

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

nästa order som placeras i butiken med *ID=1* får *ID \#100002000*.

## Ytterligare rekommenderade steg i produktionsmiljön (Cloud)

Innan vi kör `ALTER TABLE`-frågan i Adobe Commerce produktionsmiljö i molninfrastrukturen rekommenderar vi att du utför följande steg:

* Testa hela proceduren för att ändra tilläggs-ID i mellanlagringsmiljön
* [Skapa](/help/how-to/general/create-database-dump-on-cloud.md) en DB-säkerhetskopia som återställer din Production DB om fel uppstår

## Relaterad dokumentation

* [Skapa databasdump i Cloud](/help/how-to/general/create-database-dump-on-cloud.md) i vår kunskapsbas för support
* [SSH till din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=sv-SE) i utvecklardokumentationen
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
