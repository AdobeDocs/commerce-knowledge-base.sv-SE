---
title: '[!DNL MySQL] diskutrymme börjar ta slut på Adobe Commerce i molninfrastrukturen'
description: Den här artikeln innehåller lösningar för när du har mycket lite utrymme eller inget utrymme för  [!DNL MySQL]  på Adobe Commerce i molninfrastruktur. Symtomen kan omfatta avbrott i webbplatser, kunder som inte kan lägga till produkter i kundvagnen, som inte kan ansluta till databasen, få fjärråtkomst till databasen och som inte kan ansluta SSH till noden. Symtomen är också Galera, miljösynkronisering, PHP, databas och distributionsfel som listas nedan. Klicka på [Lösning](https://support.magento.com/hc/en-us/articles/360058472572#solution) för att gå direkt till lösningsavsnittet.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 660c463850abc145a22c34174aff45ac5ede6707
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 0%

---

# [!DNL MySQL] diskutrymme börjar ta slut på Adobe Commerce i molninfrastrukturen

Den här artikeln innehåller lösningar för när du har mycket lite utrymme eller inget utrymme för [!DNL MySQL] på Adobe Commerce i molninfrastruktur. Symtomen är bland annat avbrott på webbplatsen, kunder som inte kan lägga till produkter i kundvagnen, som inte kan ansluta till databasen, fjärråtkomst till databasen och som inte kan använda SSH i noden. Symtomen är också Galera, miljösynkronisering, PHP, databas och distributionsfel som listas nedan. Klicka på [Lösning](https://support.magento.com/hc/en-us/articles/360058472572#solution) om du vill gå direkt till lösningsavsnittet.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Problem

Databasen blir för stor. Symtomen kan vara att databasanslutningen bryts, databasöverföringsfel och många andra problem.

Fel som kan uppstå:

Galera:

* *SQLSTATE\[08S01\]: Kommunikationslänksfel: 1047 WSREP har inte förberetts för programanvändning än*   *Importfel:*
* *SQLSTATE\[HY000\]: Allmänt fel: 1180 Fel 5 &quot;Indata-/utdatafel&quot;* uppstod
* *SQLSTATE\[08S01\]: Kommunikationslänksfel: 1047 WSREP har inte förberetts för programanvändning än*

Fel vid miljösynkronisering:

* *SQLSTATE: Allmänt fel: 1180 Fel 5 &quot;Indata-/utdatafel&quot; uppstod under COMMIT*

PHP-fel:

* *php: SUB::\_\_construct(): [!DNL MySQL]-servern har försvunnit.*
* *php-fel: SUB::\_\_construct(): Fel vid läsning av gratulationspaket. PID=NNNN.*
* *FEL 2013 (HY000): Anslutningen till [!DNL MySQL]-servern bröts vid &#39;Läser ursprungligt kommunikationspaket&#39;, systemfel: 0 &quot;Internt fel/kontroll (inte systemfel)&quot;.*

Databasfel:

* *Fel\_kod: 1114*
* *InnoDB: Fel (slut på diskutrymme) vid skrivning av ordnod till FTS-tilläggsindextabell.*
* *SQLSTATE\[HY000\]: Allmänt fel: 2006 [!DNL MySQL]-servern har försvunnit*
* *\[ERROR\] Slav SQL: Felet &quot;Tabellen `<table\_name>` är full&quot; i frågan.*
* *Enheten mysql.service har försatts i ett felaktigt tillstånd.*
* *fel: Det går inte att ansluta till den lokala [!DNL MySQL]-servern via socketen /var/run/mysqld/mysqld.sock (111 Anslutning nekad)*
* *1205 Tidsgränsen för låsning har överskridits. Försök starta om transaktionen. Frågan var: INSERT INTO \`cron\_schedule\` (\`job\_code\`, \`status\`, \`created\_at\`, \`edul\_at\`) VÄRDEN (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Distributionsfel:

* *E: Kommandot &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; returnerade en avslutningsstatus som inte är noll 255*
* *E: Kommandot &#39;\[&#39;ssh&#39;&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 launch site-`<environment name>`g-nginx&#39;\]&#39; returnerade inte-noll*
* *Uppgraderar schema.. SQLSTATE\[HY000\]: Allmänt fel: 114 Tabellen `<table\_name>` är full*
* *SQLSTATE\[HY000\]: Allmänt fel: 3 Fel vid skrivning av fil ./`<environment name>`/\#*
* *W: `<filename>` (Felkod: 28 &quot;Inget utrymme återstår på enheten&quot;)* *Indexeringsfel (tillsammans med tillfälliga Ibd-filer som inte har sparats in i /tmp):*
* *Katalogregelindexeraren genererar ett undantag. De temporära tabellerna rensas inte i efterbearbetningen och fyller sedan i disken på den aktuella [!DNL MySQL]-huvudnoden*

<u>Steg som ska återskapas</u>:

Ett sätt att kontrollera om datalagringen `/data/mysql` (eller där [!DNL MySQL] är konfigurerad) är full är att köra följande kommando i CLI:

```bash
df -h
```

Mindre än 10 % av det lediga minnet på disken [!DNL MySQL] är en primär indikator på ett driftstopp.

## Orsak

Monteringen `/data/mysql` kan bli full på grund av en rad problem, som att det inte finns tillräckligt med noder, tillgängligt lagringsutrymme och felaktiga frågor som genererar tillfälliga tabeller.

## Lösning

Det finns ett omedelbart steg som du kan ta för att få [!DNL MySQL] tillbaka på spår (eller förhindra att den fastnar): frigör utrymme genom att tömma stora tabeller.

Men en långsiktig lösning skulle allokera mer utrymme och följa [Bästa praxis för databaser](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html), inklusive aktivering av funktionen [Arkiv för beställning/faktura/leverans](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

Här följer information om både snabba och långsiktiga lösningar.

### Kontrollera och frigöra noder

Se till att det finns tillräckligt med tillgängliga noder. Kör följande kommando för att göra detta:

```bash
df -i
```

Utdata skulle se ut ungefär så här:

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Kontrollera att Använd % är &lt;70 %. Inoder är korrelerade med filer. Om du tar bort filer från partitionen kommer du att frigöra noder.

### Kontrollera och frigör lagringsutrymme

Kontrollera tillgängligt lagringsutrymme. Kör för detta:

```bash
df -k
```

Resultatet skulle se ut ungefär så här:

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

Om Använd % är >70 % måste du vidta åtgärder för att frigöra/lägga till utrymme.

### Sök efter stora `ibtmp1` filer

Kontrollera om det finns stora `ibtmp1`-filer på `/data/mysql` i varje nod: det här är tabellutrymmet för temporära tabeller. Om det finns felaktiga frågor som genererar tillfälliga tabeller finns de i filen `ibtmp1`. Den här filen tas bara bort när databasen startas om. Om det tar upp allt tillgängligt utrymme måste databasen startas om. Om det finns felaktiga frågor återskapas den igen.

### Töm stora tabeller

>[!WARNING]
>
>Vi rekommenderar starkt att du skapar en säkerhetskopia av databasen innan du utför några ändringar och undviker dem under höga belastningsperioder på platsen. Se [Dumpa databasen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) i utvecklardokumentationen.

Kontrollera om det finns stora tabeller och tänk på om någon av dem kan tömmas. Gör detta på den primära (käll-) noden.

Tabeller med rapporter kan till exempel oftast tömmas. Mer information om hur du söker efter stora tabeller finns i artikeln [Sök efter stora [!DNL MySQL] tabeller](/help/how-to/general/find-large-mysql-tables.md) .

Om det inte finns några stora rapporttabeller bör du överväga att tömma `_index`-tabeller, bara för att returnera Adobe Commerce-programmet på rätt spår. `index_price` tabeller skulle vara de bästa kandidaterna. Exempel: `catalog_category_product_index_storeX` tabeller, där X kan ha värden från &quot;1&quot; till det maximala antalet arkiv. Tänk på att du måste indexera om för att återställa data i dessa tabeller, och om det gäller stora kataloger kan omindexeringen ta lång tid.

När du har tömt dem väntar du på att wsrep-synkroniseringen ska slutföras. Nu kan du skapa säkerhetskopior och utföra fler viktiga steg för att lägga till mer utrymme, som att allokera/köpa mer utrymme och aktivera funktionen [Arkiv för beställning/faktura/leverans](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

### Kontrollera inställningar för binär loggning

Kontrollera de binära loggningsinställningarna för [!DNL MySQL]-servern: `log_bin` och `log_bin_index`. Om inställningarna är aktiverade kan loggfilerna bli enorma. [Skapa en supportbiljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) som begär att stora binära loggfiler ska rensas. Begär också att du kontrollerar att binär loggning konfigureras korrekt så att loggarna rensas regelbundet och inte tar för mycket utrymme.

Om du inte har tillgång till serverinställningarna för [!DNL MySQL] ber du support att kontrollera det.

### Frigör oanvänt allokerat diskutrymme

1. SSH in i nod ett och loggar in på MySQL:

   ```sh
   mysql -h127.0.0.1 -p`php -r "echo (include('app/etc/env.php'))['db']['connection']['default']['password'];"` -u`whoami` `whoami`
   ```

   Detaljerade anvisningar finns i [Ansluta och köra frågor mot Adobe Commerce-databasen](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/backend-development/remote-db-connection-execute-queries).

1. Sök efter oanvänt utrymme:

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) AS size_MB, round((data_free)/1048576,2) AS Allocated_but_unused FROM information_schema.tables WHERE data_free > 1048576*10 ORDER BY data_free DESC;
   ```


   Exempelutdata:

   | table_name | size_MB | Allocated_but_unknown |
   |----------------------|----------|--------------------------|
   | sales_order_grid | 28145,20 | 14943,00 |


   Kontrollera utdata för att se om det finns minne som har allokerats men inte används. Detta inträffar när data har tagits bort från en tabell, men minnet fortfarande är allokerat till den tabellen.


1. Placera platsen i underhållsläge och stoppa kroniska jobb så att det inte sker några interaktioner i databasen. Anvisningar finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) och [Inaktivera cron-jobb](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs).
1. Frigör det utrymmet genom att återskapa tabellen med följande kommando (exempel: använd tabellen ovan med det mest oanvända utrymmet):

   ```sql
   ALTER TABLE sales_order_grid Engine = "INNODB";
   ```

1. Kör följande fråga för att kontrollera om det finns oallokerat utrymme för varje tabell som visar ett högt värde i kolumnen **[!UICONTROL Allocated_but_unused]**.

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) as size_MB, round((data_free)/1048576,2) as Allocated_but_unused FROM information_schema.tables WHERE 1 AND data_free > 1048576*10 ORDER BY 
   data_free DESC;
   ```


1. [Inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#enable-or-disable-maintenance-mode-1) och [Aktivera cron-jobb](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs).


### Allokera/köp mer utrymme

Allokera mer diskutrymme för [!DNL MySQL] om du inte har använt något. Mer information om hur du kontrollerar om det finns ledigt diskutrymme finns i artikeln [Kontrollera begränsning av diskutrymme](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md).

* För Starter-planen, alla miljöer och Pro-planintegreringsmiljöer kan du allokera diskutrymmet om du inte använder något. Mer information finns i [Allokera mer utrymme för [!DNL MySQL]](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* För Pro-planmiljöer för mellanlagrings- och produktionsmiljöer [kontaktar du support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att tilldela mer diskutrymme om du inte har använt något.

Om du har nått din utrymmesgräns och fortfarande har problem med lite utrymme kan du överväga att köpa mer diskutrymme. Kontakta Adobe Account Team för mer information.

## Relaterad läsning

[Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
