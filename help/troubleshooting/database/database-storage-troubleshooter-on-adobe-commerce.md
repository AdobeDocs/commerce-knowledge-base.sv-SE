---
title: Felsökare för databaslagring på Adobe Commerce
description: Den här artikeln är ett felsökningsverktyg för kunder som har problem med databaser i Adobe Commerce. Klicka på varje fråga för att visa svaret i varje steg i felsökaren. Beroende på dina symtom och din konfiguration visar felsökaren hur du felsöker utrymmes- och konfigurationsproblem med databaser.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Felsökare för databaslagring på Adobe Commerce

Den här artikeln är ett felsökningsverktyg för kunder som har problem med databaser i Adobe Commerce. Klicka på varje fråga för att visa svaret i varje steg i felsökaren. Beroende på dina symtom och din konfiguration visar felsökaren hur du felsöker utrymmes- och konfigurationsproblem med databaser.

## Steg 1 - Identifiera katalogen med ett utrymmesproblem {#step-1}

+++**Har du ett `/tmp`-problem som orsakas av otillräckligt utrymme?**

Detta kan indikeras av en rad symtom som att `/tmp`-monteringen är full, att platsen är nere eller att SSH inte kan placeras i en nod. Det kan också uppstå fel som _Inget utrymme kvar på enheten (28)_. En lista med fel som beror på att `/tmp` är full finns i [/tmp-monteringen full](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

Eller har du ett `/data/mysql`-problem på grund av otillräckligt utrymme? Detta kan också indikeras av en mängd olika symtom, bland annat ett webbplatsavbrott, kunder som inte kan lägga till produkter i kundvagnen, anslutningsfel i databasen och Galeriafel som _SQLSTATE\[08S01\]: Kommunikationslänksfel: 1047 WSREP_. En lista över fel som beror på brist på [!DNL MySQL] diskutrymme finns i [[!DNL MySQL] det är ont om diskutrymme på Adobe Commerce i molninfrastrukturen](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Om du är osäker på om du har ett problem med diskutrymme och har ett New Relic-konto går du till [sidan New Relic Infrastructure Monitoring Hosts](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). Därifrån klickar du på fliken **Lagring**, ändrar listrutan **Diagramvisning** från 5 till 20 resultat och letar i tabellen efter hög diskanvändning i tabellen eller tabellen Diskanvändning. Mer detaljerad information finns i [New Relic Infrastructure Monitoring (Infrastrukturövervakning) > fliken Storage (Lagring)]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Om du har något av de symtom som beskrivs ovan bör du kontrollera status på dina noder för att kontrollera att det inte beror på problem med filnummer. Om du vill göra det kör du följande kommando i CLI/Terminal:\
`df -ih`

Är IUse% > 90%?

a. JA - Detta beror på att det finns för många filer. Granska stegen för att ta bort filer på ett säkert sätt i [Ta bort filer när det inte finns tillräckligt med diskutrymme, Adobe Commerce i molninfrastrukturen](https://experienceleague.adobe.com/sv/docs/experience-cloud-kcs/kbarticles/ka-26889). Fortsätt till [Steg 2](#step-2) när du har slutfört de här stegen. [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om du vill begära mer utrymme.\
b. NEJ - Kontrollera utrymmet. Kör `df -h | grep mysql` och sedan `df -h | grep tmp` i CLI/Terminal för att kontrollera diskutrymmesanvändningen i katalogerna `/tmp` och `/data/mysql`. Fortsätt till [Steg 3](#step-3).

+++

## Steg 2 - Kontrollera diskutrymme {#step-2}

+++**Kontrollera användning av diskutrymme?**

När du har minskat antalet filer kör du `df -h | grep mysql` och sedan `df -h | grep tmp` i CLI/Terminal för att kontrollera diskutrymmesanvändningen i `/tmp` och `/data/mysql`. Används mer än 70 % för `/tmp` eller `/data/mysql`?

a. JA - Fortsätt till [steg 3](#step-3).
b. NEJ - Frågor kan ta slut på det tillgängliga lagringsutrymmet. Detta kan krascha noden, ta bort frågan och ta bort `tmp`-filerna. Granska utdata för `SHOW PROCESSLIST;` i CLI:n för [!DNL MySQL] efter frågor som kan vara orsaken till problemet. [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och begär mer utrymme.

+++

## Steg 3 - Identifiera katalog med hög användning {#step-3}

+++**Vilken katalog används till mer än 70 %?**

Vilken katalog används till mer än 70 %? `/tmp` eller `/data/mysql`?

>[!NOTE]
>
>Som standard skriver tmpdir till `/tmp`. Om du vill kontrollera att din databaskonfiguration fortfarande är på den här standardinställningen kör du följande kommando i [!DNL MySQL] CLI: `SHOW VARIABLES LIKE "TMPDIR";` Om databasens tmpdir fortfarande skriver till `/tmp` visas `/tmp` i värdekolumnen.

a. `/tmp` - Fortsätt till [Steg 4](#step-4). \
b. `/data/mysql` - Fortsätt till [Steg 5](#step-5).

+++

## Steg 4 - felsökning/tmp-montering full {#step-4}

+++**Felsök /tmp-montering full**

[Felsök/tmp-monteringen fullt för Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), bläddra nedåt i artikeln och prova lösningarna och bästa praxis. Kör sedan `df -h | grep mysql` och `df -h | grep tmp` i CLI/Terminal för att kontrollera diskutrymmesanvändningen i `/tmp`- och `/data/mysql`-kataloger\
  &lt; 70 % används?

>[!NOTE]
>
>Lösningarna i [Felsök/tmp-paketet fullt för Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) är utformade för handlare som inte har ändrat variablerna för databas-tmpdir, som som standard skriver till `/tmp`. Om du har ändrat tmpdir-värdet är instruktionerna i [Felsök/tmp-paketet fullt för Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) inte till någon hjälp.

a. JA - Du har löst problemet. \
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och begär mer utrymme.

+++

## Steg 5 - Kontrollera standard {#step-5}

+++**Kontrollera standard**

Databaskonfigurationen kanske inte längre är den ursprungliga standardinställningen. Hitta tmpdir-konfigurationen för databasen genom att köra i [!DNL MySQL] CLI: `SELECT @@DATADIR;`. Om `/data/mysql/` är utdata skrivs databasens tmpdir nu till `/data/mysql/`. Försök att öka utrymmet i den här katalogen genom att följa stegen i [[!DNL MySQL] diskutrymmet börjar ta slut på Adobe Commerce i vår molninfrastruktur](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). Kör sedan `df -h | grep mysql` och `df -h | grep tmp` i CLI/Terminal för att kontrollera diskutrymmesanvändningen i `/data/mysql` och `/tmp`.\
  &lt; 70 % används?

a. JA - Du har löst problemet. \
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och begär mer utrymme.

+++

[Tillbaka till steg 1](#step-1)

## Relaterad läsning

* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
