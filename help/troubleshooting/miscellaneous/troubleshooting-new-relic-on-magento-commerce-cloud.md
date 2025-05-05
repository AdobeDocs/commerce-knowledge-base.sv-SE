---
title: Felsöka New Relic på Adobe Commerce i molninfrastruktur
description: I den här artikeln finns resurser för att felsöka New Relic i Adobe Commerce om molninfrastruktur.
exl-id: ea763291-5c9b-4575-b2ee-820dbc367743
feature: Cloud, Observability, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Felsöka New Relic på Adobe Commerce i molninfrastruktur

I den här artikeln finns resurser för att felsöka New Relic i Adobe Commerce om molninfrastruktur.

<table>
<tbody>
<tr>
<td class="wysiwyg-text-align-center"><strong>Problem</strong></td>
<td class="wysiwyg-text-align-center"><strong>Orsak</strong></td>
<td class="wysiwyg-text-align-center"><strong>Resurs</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Åtkomstproblem</td>
</tr>
<tr>
<td>
<p><u>Kan inte se projekt i New Relic.</u></p>
<p>Du loggar in på <em>New Relic</em> men kan inte se projekt som du bör ha behörighet att visa/komma åt.</p>
</td>
<td>
<p>I sådana fall måste en administratörsanvändare lägga till dig i projektet.</p>
</td>
<td>
<p><a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html?lang=sv-SE">Åtkomst till New Relic-tjänster</a> i vår kunskapsbas för support.</p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Dataproblem</td>
</tr>
<tr>
<td>
<p><u>Data saknas efter installationen.</u></p>
<p>Använd verktyget <a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/new-relic-diagnostics">New Relic Diagnostics</a> för att försöka identifiera orsaken. Om detta inte hjälper kan du titta närmare på agentspecifika lösningar. Länkar till artiklar som innehåller dessa lösningar finns i den högra kolumnen.</p>
</td>
<td>
<p>Saknade data kan ha olika orsaker. Du kan behöva:</p>
<ul>
<li>Kontrollera att agenten är installerad.</li>
<li>Verifiera programnamnet och licensnyckeln.</li>
<li>Starta om webbservern.</li>
<li>Kontrollera att systemet uppfyller kompatibilitetskraven.</li>
<li>INI-inställningar.</li>
</ul>
</td>
<td>
<ul>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#apm-agents">New Relic Documentation &gt; APM Agents &gt; Not Seeing Data</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#browser-agent">New Relic Documentation &gt; New Relic Browser &gt; Not See Data</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#infrastructure-agents">New Relic Documentation &gt; New Relic Infrastructure &gt; Not Seeing Data</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#mobile-agents">New Relic Documentation &gt; New Relic Mobile &gt; Not Seeing Data</a></li>
</ul>
</td>
</tr>
<tr>
<td>
<p><u>Tidsstämpelfel för transaktioner.</u> Det kan vara svårt att hitta långa transaktioner (mer än fem minuter) med New Relic-gränssnittet. Du kan också hitta transaktioner som visas utanför den förväntade tidsramen.</p>
</td>
<td>
<p>I New Relic-gränssnittet visas tidpunkten för transaktionens slut, inte tidpunkten då transaktionen påbörjades.</p>
</td>
<td>
<p>Om du vill beräkna början av transaktionen med hjälp av användargränssnittet i New Relic ska du kontrollera transaktionens varaktighet. Subtrahera varaktighetsbeloppet från tidsstämpeln (transaktionens slut) som tillhandahålls av New Relic användargränssnitt.</p>
</td>
</tr>
<tr>
<td>
<p><u>NerdGraph GraphQL <code>curl</code> -frågor som använder specialtecken som <code>|</code> och <code>%</code> fungerar inte</u>.</p>
</td>
<td>
<p>New Relic funktion "copy to curl" i NerdGraph har för närvarande inget sätt att hantera specialtecken som <code>|</code> och <code>%</code>.</p>
</td>
<td>
<p>Använd ett annat API-bibliotek för att lösa problemet med specialtecken. Exempel: GraphQLClient Library för Graphql API i Python, eller Apache.Commons för Java Language-anrop. Granska klientbibliotek på <a href="https://graphql.org/code/">GraphQL</a>.</p>
</td>
</tr>
<tr>
<td>
<p><u>Problem med diagram- och instrumentpanelsvisning.</u></p>
</td>
<td>
<p>Lös saknade diagram genom att lägga till New Relic-domäner i tillåtelselista eller avinstallera det webbläsartillägg som orsakar problemen.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/apm/new-relic-apm/troubleshooting/charts-missing-or-do-not-render">New Relic Documentation &gt; Charts missing or do not render</a> </p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">PHP-agentproblem</td>
</tr>
<tr>
<td>
<p><u>PHP-agenten visar inte rätt antal instanser.</u></p>
</td>
<td>
<p>Antalet instanser kan öka beroende på back end-processer och genomströmning. Skillnader mellan servervärden kan bero på processer som körs på en server, men inte på den andra servern.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/agents/php-agent/troubleshooting/troubleshoot-php-agent-instance-count">New Relic Documentation &gt; Troubleshoot the PHP agent instance count</a> </p>
</td>
</tr>
</tbody>
</table>
