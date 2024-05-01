---
title: Felsökare för databaslagring på Adobe Commerce
description: Den här artikeln är ett felsökningsverktyg för kunder som har problem med databaser i Adobe Commerce. Klicka på varje fråga för att visa svaret i varje steg i felsökaren. Beroende på dina symtom och din konfiguration visar felsökaren hur du felsöker utrymmes- och konfigurationsproblem med databaser.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Felsökare för databaslagring på Adobe Commerce

Den här artikeln är ett felsökningsverktyg för kunder som har problem med databaser i Adobe Commerce. Klicka på varje fråga för att visa svaret i varje steg i felsökaren. Beroende på dina symtom och din konfiguration visar felsökaren hur du felsöker utrymmes- och konfigurationsproblem med databaser.

## Steg 1 - Identifiera katalogen med ett utrymmesproblem {#step-1}

+++**Har du en `/tmp` på grund av brist på utrymme?**

Detta kan indikeras av en rad olika symtom, bland annat `/tmp` som är full, plats ned eller som inte kan SSH till en nod. Du kan också råka ut för fel som _Inget utrymme kvar på enheten (28)_. För en lista över fel som uppstått `/tmp` är full, granska [/tmp full](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

Eller har du en `/data/mysql` på grund av brist på utrymme? Detta kan också indikeras av en mängd olika symtom, bland annat ett driftstopp, kunder som inte kan lägga till produkter i kundvagnen, fel i anslutningen till databasen och Galeriafel som _SQLSTATE\[08S01\]: Kommunikationslänksfel: 1047 WSREP_. En lista över fel som beror på brist på MySQL-diskutrymme finns på [Det är ont om diskutrymme på Adobe Commerce i molninfrastrukturen](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Om du är osäker på om du har ett problem med diskutrymme och har ett New Relic-konto går du till [New Relic Infrastructure Monitoring Hosts page](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). Därifrån klickar du på **Lagring** -fliken, ändra **Diagramvisning** från 5 till 20 resultat och se i tabellen hur du kan använda disken i tabellen Använda diskar i %. Mer detaljerad information finns i [New Relic Infrastructure Monitoring > fliken Storage]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Om du har något av de symtom som beskrivs ovan bör du kontrollera status på dina noder för att kontrollera att det inte beror på problem med filnummer. Om du vill göra det kör du följande kommando i CLI/Terminal:\
`df -ih`

Är IUse% > 90%?

a. JA - Detta beror på att det finns för många filer. Granska stegen för att ta bort filer säkert i [Radera filer på ett säkert sätt när det inte finns tillräckligt med diskutrymme, Adobe Commerce i molninfrastrukturen](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). Fortsätt till [Steg 2](#step-2) när du har utfört dessa steg. Om du vill ha mer utrymme [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEJ - Kontrollera utrymmet. Kör `df -h | grep mysql` och sedan `df -h | grep tmp` i CLI/Terminal för att kontrollera diskutrymmesanvändningen i `/tmp` och `/data/mysql` kataloger. Fortsätt till [Steg 3](#step-3).

+++

## Steg 2 - Kontrollera diskutrymme {#step-2}

+++**Vill du kontrollera hur mycket diskutrymme som används?**

När du har minskat antalet filer kör du `df -h | grep mysql` och sedan `df -h | grep tmp` i CLI/Terminal för att kontrollera diskutrymmesanvändningen i `/tmp` och `/data/mysql`. Är större än 70 % används för `/tmp` eller `/data/mysql`?

a. JA - Fortsätt till [Steg 3](#step-3).
b. NEJ - Frågor kan ta slut på det tillgängliga lagringsutrymmet. Detta kan krascha noden, ta bort frågan och ta bort `tmp` filer. Granska utdata från `SHOW PROCESSLIST;` i MySQL CLI för frågor som kan vara orsaken till problemet. [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), begär mer utrymme.

+++

## Steg 3 - Identifiera katalog med hög användning {#step-3}

+++**Vilken katalog används till mer än 70 %?**

Vilken katalog används till mer än 70 %? `/tmp` eller `/data/mysql`?

>[!NOTE]
>
>Standard är att tmpdir skriver till `/tmp`. Kör följande kommando i MySQL CLI om du vill kontrollera att databaskonfigurationen fortfarande är på denna standard: `SHOW VARIABLES LIKE "TMPDIR";` Om databasens tmpdir fortfarande skriver till `/tmp`kommer du att se `/tmp` i kolumnen Värde.

a. `/tmp` - Fortsätt till [Steg 4](#step-4). \
b. `/data/mysql` - Fortsätt till [Steg 5](#step-5).

+++

## Steg 4 - felsökning/tmp-montering full {#step-4}

+++**Felsökning av fullständig /tmp-montering**

[Felsök fullständigt /tmp-paket för Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md)bläddrar du nedåt i artikeln och provar lösningar och bästa praxis. Kör sedan `df -h | grep mysql` och sedan `df -h | grep tmp` i CLI/Terminal för att kontrollera diskutrymmesanvändningen i `/tmp` och `/data/mysql` kataloger\
  &lt; 70 % används?

>[!NOTE]
>
>Lösningarna i [Felsök fullständigt /tmp-paket för Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) är utformade för handlare som inte har ändrat variablerna för database tmpdir, som som standard skriver till `/tmp`. Om du har ändrat tmpdir-värdet finns instruktionerna i [Felsök fullständigt /tmp-paket för Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) kommer inte att hjälpa.

a. JA - Du har löst problemet. \
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), begär mer utrymme.

+++

## Steg 5 - Kontrollera standard {#step-5}

+++**Kontrollera standard**

Databaskonfigurationen kanske inte längre är den ursprungliga standardinställningen. Hitta tmpdir-konfigurationen för databasen genom att köra i MySQL CLI: `SELECT @@DATADIR;`. If `/data/mysql/` skrivs nu databasens tmpdir till `/data/mysql/`. Försök att öka utrymmet i den här katalogen genom att följa stegen i [Utrymmet för MySQL-disken är lågt på Adobe Commerce i vår molninfrastruktur](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). Kör sedan `df -h | grep mysql` och sedan `df -h | grep tmp` i CLI/Terminal för att kontrollera diskutrymmesanvändningen i `/data/mysql` och `/tmp`.\
  &lt; 70 % används?

a. JA - Du har löst problemet. \
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), begär mer utrymme.

+++

[Tillbaka till steg 1](#step-1)
