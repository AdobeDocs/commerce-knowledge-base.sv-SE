---
title: Felsöka prestanda med New Relic på Adobe Commerce
description: 'Den här artikeln innehåller felsökningssteg för att lösa Adobe Commerce om prestandaproblem i molninfrastruktur med New Relic. Det innehåller också resurser för mer information. Här är en lista över problem. Klicka för att se felsökningsstegen i vår kunskapsbas:'
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: 27fed162416c619a08d757279a3405f1fa72e976
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# Felsöka prestanda med New Relic på Adobe Commerce

Den här artikeln innehåller felsökningssteg för att lösa Adobe Commerce om prestandaproblem i molninfrastruktur med New Relic. Det innehåller också resurser för mer information. Följande problem med rekommenderade resurser som beskrivs i tabellen nedan är:

* Låga Apdex-poäng
* Hög användning av CPU
* Höga I/O-åtgärder
* Utfall

<table>
<tbody>
<tr>
<td>Problem</td>
<td>Felsökning</td>
<td>Resurs</td>
</tr>
<tr>
<td>
<p>Låg poäng för Apdex:</p>
<p>Din New Relic <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">Apdex-poäng</a> mäter hur nöjda användarna är med svarstiden för dina webbprogram och tjänster.</p>
</td>
<td>
<p>Du loggar in på <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Översikt. På höger sida av översiktssidan ser du diagrammet för Apdex-bakgrundsmusik. En Apdex-poäng på 0,5 eller mindre ger anledning till oro och motiverar en utredning: Web-transaction times (serverförfrågningar):</p>
<ol>
<ol>
<li>Logga in på <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (välj en app) &gt; Översikt. Se till att filtret är inställt på tiden för webbtransaktioner i listrutan för huvuddiagram. Titta efter programserverns tid i tabellen Transaktioner. Kontrollera om du har några långvariga eller misstänkta transaktioner.</li>
<li>Undersök dem individuellt genom att gå till Övervaka &gt; Transaktioner och se till att du anger filtren för webben och den mest tidskrävande <em>.</em>
</li>
<li>Sök sedan efter moduler från tredje part som förbrukar resurser: betalare, ERP osv.</li>
<li>I avsnittet Övervakning av APM:<ol>
<li>Klicka på Transaktioner.</li>
<li>Bläddra nedåt och klicka på Visa alla transaktionsregister.</li>
<li>Du kan sortera transaktioner efter <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">olika parametrar</a> och hoppa till dem som orsakar misstanke.</li>
<li>Granska transaktionerna med låga Apdex-poäng, ovanligt höga antal eller hög genomsnittlig tid, eller Dissat %.</li>
<li>Klicka på varje enskild transaktion. Om du inte kan lösa problemet kan du <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">skicka in en supportanmälan.</a>
</li>
<li>Om du behöver undersöka fler saker bör du överväga att kontrollera transaktioner som inte är webbtransaktioner.</li>
</ol>
</li>
</ol>
</ol>
<p>Tid för icke-webbtransaktioner (åtgärder och bakgrundsuppgifter):</p>
<ol>
<ol>
<li>Logga in på <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (välj en app) &gt; Översikt. Se till att du väljer Tid för icke-webbtransaktioner i listrutan för huvuddiagram. Klicka på enskilda transaktioner i transaktionsregistret. Håll utkik efter långvariga eller misstänkta transaktioner. Detta omfattar backend-jobb, cron-jobb eller import-/exportjobb, inklusive tredjepartsjobb.</li>
</ol>
</ol>
</td>
<td>
<p>Mer information om New Relic Apdex-poängen finns i <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">New Relic Documentation &gt; APM Apdex &gt; Mät användarnöjdhet</a>. Du kan även referera till <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-apdex-warning-alert">Hanterade aviseringar för Adobe Commerce: Apdex-varning</a> i vår kunskapsbas för support.</p>
</td>
</tr>
<tr>
<td>
<p>Hög CPU-användning:</p>
<p>Hög användning av CPU kan visa att det finns en särskilt upptagen tjänst, som MySQL, Redis osv.</p>
</td>
<td>
<ol>
<li>Logga in på <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastruktur &gt; Processer.</li>
<li>Granska CPU-diagram för att se om det finns några fastnade eller mycket krävande processer som använder mer än 100 % CPU-tid och jämför med processorantalet i instansen. Var uppmärksam på toppar i resursanvändningen. Vi rekommenderar inte att du avbryter en process om den inte är en ifastande kron.</li>
</ol>
</td>
<td>
<p>Mer information om prestandamått, särskilt CPU i procent, I/O-byte och minnesanvändning för enskilda eller grupper av processer finns i <a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">New Relic Documentation &gt; Infrastructure UI page &gt; Infrastructure Host page &gt; Processes tab</a>.</p>
</td>
</tr>
<tr>
<td>
<p>Hög I/O-drift: För varje kund är det här antalet individuellt men skiljer sig avsevärt från genomsnittet.</p>
</td>
<td>
<p>Håll utkik efter en ovanlig topp jämfört med tidigare genomsnittliga I/O-åtgärder:</p>
<ol>
<li>Logga in på <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastruktur &gt; Processer.</li>
<li>Granska I/O-lästa byte per sekund-diagram.</li>
<li>Registrera tidpunkten för toppen.</li>
<li>Klicka på APM.</li>
<li>Se till att du väljer tid för webbtransaktioner i listrutan för huvuddiagram.</li>
<li>Ange tiden för tidpunkten för den tagg du spelade in.</li>
<li>Sök efter transaktioner som har orsakat höga I/O-åtgärder.</li>
<li>Granska alla transaktionsspår &gt; Spårningsdetaljer för att hitta vad som kan orsaka problem.</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>Utfall: New Relic fastställer avbrott per Apdex. En röd linje visas i Apdex-poängdiagrammet, vilket anger att Apdex är &lt; 0.4, vilket anses vara ett avbrott.</p>
</td>
<td>
<p>Att undersöka ett driftstopp kan ta flera steg, nämligen att undersöka webb- och icke-webbtransaktioner, databaser och tredjepartstransaktioner. Webbtransaktioner:</p>
<ol>
<li>Logga in på <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Översikt. Se till att filtret är inställt på tiden för webbtransaktioner i det nedrullningsbara diagramfiltret.</li>
<li>Begränsa tidsfönstret manuellt.</li>
<li>Klicka på Transaktioner. Kontrollera att filtren är inställda på Webb och att de är mest tidskrävande. Undersök den senaste transaktionen.</li>
<li>Om du behöver undersöka fler saker bör du överväga att kontrollera transaktioner som inte är webbtransaktioner.</li>
</ol>
<p>Icke-webbtransaktioner:</p>
<ol>
<li>Gå tillbaka till sidan Översikt och växla till transaktioner som inte är webbtransaktioner i listrutan.</li>
<li>Granska transaktionsspårningar längst ned på sidan, en i taget.</li>
<li>Beroende på vad problemet är kan du behöva använda ett tredjepartsverktyg som en PHP-profilerare för att hitta en flaskhals.</li>
<li>Om du behöver undersöka mer kan du överväga att undersöka databasprocesserna.</li>
</ol>
<p>Databasprocesser:</p>
<ol>
<li>Gå till Övervakning &gt; Databaser på APM-sidan.</li>
<li>Sortera efter Användare.</li>
<li>Granska de vanligaste frågorna.

Obs! <code>UPPDATERA</code> eller <code>INFOGA</code>frågor är de mest CPU-krävande frågorna.</li>
<li>Växla till Genomflöde från Sortera efter väljare och sök efter processer som har orsakat databasens genomströmning till listruta.</li>
<li>Om du behöver utforska mer kan du överväga att undersöka tredjepartstjänster.</li>
</ol>
<p>Tredjepartstjänster:</p>
<ol>
<li>Gå till Övervakning &gt; Externa tjänster på APM-sidan.</li>
<li>Välj den långsammaste genomsnittliga svarstiden i listrutan Sortera efter.</li>
<li>Sök efter processer som inträffade precis före driftstoppet.</li>
</ol>
</td>
<td>
<p>Mer information om hur du undersöker specifika prestandaproblem finns i <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">New Relic Documentation &gt; APM UI pages &gt; Transactions page &gt; Use drill down functions</a>.</p>
</td>
</tr>
</tbody>
</table>
