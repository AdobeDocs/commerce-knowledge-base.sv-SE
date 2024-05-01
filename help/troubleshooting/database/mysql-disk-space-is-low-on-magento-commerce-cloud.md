---
title: Det är ont om diskutrymme på Adobe Commerce i molninfrastrukturen
description: Den här artikeln innehåller lösningar för när du har mycket lite utrymme eller inte har något utrymme för MySQL på Adobe Commerce i molninfrastruktur. Symtomen kan omfatta avbrott i webbplatser, kunder som inte kan lägga till produkter i kundvagnen, som inte kan ansluta till databasen, få fjärråtkomst till databasen och som inte kan ansluta SSH till noden. Symtomen är också Galera, miljösynkronisering, PHP, databas och distributionsfel som listas nedan. Klicka på [Lösning](https://support.magento.com/hc/en-us/articles/360058472572#solution) för att gå direkt till lösningsavsnittet.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 0%

---

# Det är ont om diskutrymme på Adobe Commerce i molninfrastrukturen

Den här artikeln innehåller lösningar för när du har mycket lite utrymme eller inte har något utrymme för MySQL på Adobe Commerce i molninfrastruktur. Symtomen kan omfatta avbrott i webbplatser, kunder som inte kan lägga till produkter i kundvagnen, som inte kan ansluta till databasen, få fjärråtkomst till databasen och som inte kan ansluta SSH till noden. Symtomen är också Galera, miljösynkronisering, PHP, databas och distributionsfel som listas nedan. Klicka [Lösning](https://support.magento.com/hc/en-us/articles/360058472572#solution) för att gå direkt till lösningssektionen.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Problem

Databasen blir för stor. Symtomen kan vara att databasanslutningen bryts, databasöverföringsfel och många andra problem.

Fel som kan uppstå:

Galera:

* *SQLSTATE\[08S01\]: Kommunikationslänksfel: 1047 WSREP har ännu inte förberetts för programanvändning*   *Importfel:*
* *SQLSTATE\[HY000\]: Allmänt fel: 1180 Fel 5 &quot;Indata-/utdatafel&quot;*
* *SQLSTATE\[08S01\]: Kommunikationslänksfel: 1047 WSREP har ännu inte förberetts för programanvändning*

Fel vid miljösynkronisering:

* *SQLSTATE: Allmänt fel: 1180 Fel 5 &quot;Indata-/utdatafel&quot; uppstod under COMMIT*

PHP-fel:

* *php: SUB:::\_\_construct(): MySQL-servern har försvunnit.*
* *php-fel: SUB::\_\_construct(): Fel vid läsning av gratulationspaket. PID=NNNN.*
* *FEL 2013 (HY000): Anslutningen till MySQL-servern bröts vid &#39;läsning av ursprungligt kommunikationspaket&#39;, systemfel: 0 &quot;Internt fel/kontroll (inte systemfel)&quot;.*

Databasfel:

* *Fel\_kod: 1114*
* *InnoDB: Fel (slut på diskutrymme) vid skrivning av ordnod till FTS-tilläggsindextabell.*
* *SQLSTATE\[HY000\]: Allmänt fel: 2006 MySQL-servern har försvunnit*
* *\[ERROR\] Slave SQL: Error &#39;The table `<table\_name>` är full vid fråga.*
* *Enheten mysql.service har försatts i ett felaktigt tillstånd.*
* *fel: &#39;Det går inte att ansluta till den lokala MySQL-servern via socketen &#39;/var/run/mysqld/mysqld.sock&#39; (111 &quot;Anslutning nekad&quot;)&#39;*
* *1205 Tidsgränsen för låsningen har överskridits. Försök starta om transaktionen. Frågan var: INSERT INTO \`cron\_schedule\` (\`job\_code\`, \`status\`, \`created\_at\`, \`schedule\_at\`) VÄRDEN (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Distributionsfel:

* *E: Kommandot &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; returnerade avslutningsstatus 255 som inte var noll*
* *E: Kommando &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 start site-`<environment name>`g-nginx&#39;\]&#39; returnerade icke-noll*
* *Uppgraderar schema.. SQLSTATE\[HY000\]: Allmänt fel: 1114 Tabellen `<table\_name>` är full*
* *SQLSTATE\[HY000\]: Allmänt fel: 3 Fel vid skrivning av fil./`<environment name>`/\#*
* *B: `<filename>` (Felkod: 28&quot;Inget utrymme kvar på enheten&quot;)*  *Indexeringsfel (tillsammans med överblivna tillfälliga .ibd-filer i /tmp):*
* *Katalogregelindexeraren genererar ett undantag. De temporära tabellerna rensas inte i eftermatningen och fyller sedan i disken på den aktuella MySQL-huvudnoden*

<u>Steg som ska återskapas</u>:

Ett sätt att kontrollera om `/data/mysql` (eller där MySQL-datalagring är konfigurerad) är full genom att köra följande kommando i CLI:

```bash
df -h
```

Mindre än 10 % av det lediga minnet på MySQL-disken är en primär indikator på ett driftstopp.

## Orsak

The `/data/mysql` Monteringen kan bli full på grund av en rad problem, som att det inte finns tillräckligt med noder, tillgängligt lagringsutrymme och felaktiga frågor som genererar tillfälliga tabeller.

## Lösning

Det finns ett omedelbart steg som du kan ta för att få tillbaka MySQL på spåret (eller förhindra att det fastnar): frigör utrymme genom att tömma stora tabeller.

Men en långsiktig lösning skulle ge mer utrymme och [Bästa praxis för databaser](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html), inklusive att [Arkiv för order/faktura/utleverans](https://docs.magento.com/user-guide/sales/order-archive.html) funktionalitet.

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

### Kontrollera om det finns stora `ibtmp1` filer

Kontrollera om det finns stora `ibtmp1` fil på `/data/mysql` för varje nod: den här filen är tabellutrymmet för temporära tabeller. Om det finns felaktiga frågor som genererar tillfälliga tabeller finns de i `ibtmp1` -fil. Den här filen tas bara bort när databasen startas om. Om det tar upp allt tillgängligt utrymme måste databasen startas om. Om det finns felaktiga frågor återskapas den igen.

### Töm stora tabeller

>[!WARNING]
>
>Vi rekommenderar starkt att du skapar en säkerhetskopia av databasen innan du utför några ändringar och undviker dem under höga belastningsperioder på platsen. Se [Dumpa databasen](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump) i vår dokumentation för utvecklare.

Kontrollera om det finns stora tabeller och tänk på om någon av dem kan tömmas. Gör detta på den primära (käll-) noden.

Tabeller med rapporter kan till exempel oftast tömmas. Mer information om hur du söker efter stora tabeller finns i [Sök efter stora MySQL-tabeller](/help/how-to/general/find-large-mysql-tables.md) artikel.

Om det inte finns några stora rapporttabeller bör du överväga att tömma `_index` bara för att returnera Adobe Commerce-programmet på rätt spår. `index_price` tabeller skulle vara de bästa kandidaterna. Till exempel: `catalog_category_product_index_storeX` tabeller, där X kan ha värden från &quot;1&quot; till det maximala antalet butiker. Tänk på att du måste indexera om för att återställa data i dessa tabeller, och om det gäller stora kataloger kan omindexeringen ta lång tid.

När du har tömt dem väntar du på att wsrep-synkroniseringen ska slutföras. Nu kan du skapa säkerhetskopior och göra mer, till exempel tilldela/köpa mer utrymme och aktivera [Arkiv för order/faktura/utleverans](https://docs.magento.com/user-guide/sales/order-archive.html) funktionalitet.

### Kontrollera inställningar för binär loggning

Kontrollera binära loggningsinställningar för MySQL-servern: `log_bin` och `log_bin_index`. Om inställningarna är aktiverade kan loggfilerna bli enorma. [Skapa en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) begär att stora binära loggfiler ska rensas. Begär också att du kontrollerar att binär loggning konfigureras korrekt så att loggarna rensas regelbundet och inte tar för mycket utrymme.

Om du inte har tillgång till inställningarna för MySQL-servern ber du support att kontrollera dem.

### Allokera/köp mer utrymme

Allokera mer diskutrymme för MySQL om du inte har använt något. Se [Kontrollera diskutrymmesgräns](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) om du vill veta mer om hur du kontrollerar om det finns ledigt diskutrymme.

* För Starter-planen, alla miljöer och Pro-planintegreringsmiljöer kan du allokera diskutrymmet om du inte använder något. Mer information finns i [Allokera mer utrymme för MySQL](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* För Pro-planmiljöer: [kontakta support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om du vill tilldela mer diskutrymme om du inte har använt något.

Om du har nått din utrymmesgräns och fortfarande har problem med lite utrymme kan du överväga att köpa mer diskutrymme. Kontakta Adobe Account Team för mer information.
