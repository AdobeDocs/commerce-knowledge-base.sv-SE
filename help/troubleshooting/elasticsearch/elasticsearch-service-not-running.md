---
title: Tjänsten Elasticsearch körs inte
description: Den här artikeln innehåller lösningar på fel som kan uppstå när tjänsten Elasticsearch (ES) inte körs (vanligtvis som ett resultat av krascher). Symtomen kan vara fel vid hälsokontroller som körs med vändning, omindexering med kommandoraden, undantag- och PHP-fel samt fel på produktsidor. I tabellen visas fel och länkar till resurser som du kan försöka åtgärda. Ett symtom kan ha en rad olika orsaker.
exl-id: 2c2230de-cb30-4a03-8c3e-d9f44783dbae
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Tjänsten Elasticsearch körs inte

Den här artikeln innehåller lösningar på fel som kan uppstå när tjänsten Elasticsearch (ES) inte körs (vanligtvis som ett resultat av krascher). Symtomen kan vara fel vid hälsokontroller som körs med vändning, omindexering med kommandoraden, undantag- och PHP-fel samt fel på produktsidor. I tabellen visas fel och länkar till resurser som du kan försöka åtgärda. Ett symtom kan ha en rad olika orsaker.

## Versionskompatibilitet för Elasticsearch med Adobe Commerce

* Adobe Commerce lokalt och Adobe Commerce i molninfrastruktur:

   * v2.2.3+ stödjer ES 5.x
   * v2.2.8+ och v2.3.1+ har stöd för ES 6.x
   * ES v2.x och v5.x rekommenderas inte på grund av [slutet på livscykeln](https://www.elastic.co/support/eol). Om du har Adobe Commerce v2.3.1 och vill använda ES 2.x eller ES 5.x måste du [Ändra Elasticsearch PHP-klienten](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

* Magento Open Source v2.3.0+ stöder ES 5.x och 6.x (men 6.x rekommenderas).

<table>
<tr>
<th>Symtom när ES-tjänsten inte körs</th>
<th>Information</th>
<th>Resurs</th>
</tr>
<tr>
<td rowspan="3">Undantagsfel</td>
</tr>
<tr>
<td>
<code>{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}]</code>
</td>
<td>
<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsearch-5-is-configured-but-search-page-does-not-load-with-fielddata-is-disabled...-error.html">Elasticsearch 5 har konfigurerats, men söksidan läses inte in med felmeddelandet "FieldData is disabled..." </a> i vår kunskapsbas för support.
</td>
</tr>
<tr>
<td>
<code>Elasticsearch\Common\Exceptions\NoNodesAvailableException: Noticed exception 'Elasticsearch\Common\Exceptions\NoNodesAvailableException' with message 'No alive nodes found in your cluster' in /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/ConnectionPool/StaticNoPingConnectionPool.php:51</code>
</td>
<td>
Elasticsuite-index tas inte bort.  Se <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">Spårningsindex för ElasticSuite orsakar problem med Elasticsearch</a> i vår kunskapsbas för support.
 </td>
</tr>
<tr>
<td>PHP-fel</td>
<td>
<i>Inga aktiva noder hittades i ditt kluster","1":"#0 /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/Transport.php</i>
</td>
<td rowspan="4">
<ul>
<li>Resurser för otillräckligt diskutrymme:<ul>
<li><a href="https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/">8 tips för att lösa problem med hårddisken i Linux och Unix, t.ex. när disken är full eller inte kan skriva till disken</a></li>
<li><a href="https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not">serverdefault: df says disk is full, but it is not</a></li>
<li><a href="https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux">unix.stackexchange.com: Spåra var diskutrymmet har pågått i Linux?</a></li>
<li>Loggfiler arkiveras inte tillräckligt ofta. Se <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/systems/action-logs/action-log-archive">Konfigurera loggarkivet</a> i utvecklardokumentationen.</li>
<li>Filsystemkataloger är inte optimerade. Se <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#resource-file-optimization">Filoptimering</a> i utvecklardokumentationen.</li>
<li>Om lösningarna i ovanstående dokumentation inte löser problemet kan du kontakta ditt Adobe-kontoteam för att begära ytterligare lagringsutrymme.</li>
</ul>
</li>
<li>Om disken inte har slut på lagringsutrymme men du fortfarande får felmeddelanden i den vänstra kolumnen, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">skickar du en supportanmälan</a>.</li>
</ul>
<ul>
<li>Se <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">Spårningsindex för ElasticSuite orsakar problem med Elasticsearch</a> i vår kunskapsbas för support.
</li>
</ul>
</td>
</tr>
<tr>
<td><code>Curl</code> fel</td>
<td>Om du kör kommandot <code>curl</code> för att kontrollera Elasticsearch-hälsa:<code>curl -m1 localhost:9200/_cluster/health?pretty</code>(eller<code>curl -m1 elasticsearch.internal:9200/_cluster/health?pretty</code>för startkonton) uppstår följande fel: <i>Fel: curl: (7) Det gick inte att ansluta till localhost-port 9200: Anslutningen nekades</i> </td>
</tr>
<tr>
<td>Kommandoradsfel</td>
<td>Om <code>$ bin/magento indexer:reindex catalogsearch_fulltext</code> körs uppstår det här felet <i>Katalogsökindexerarprocessen är okänd:
        Inga aktiva noder hittades i klustret</i>
</td>
</tr>
<tr>
<td>Fel på produktsidor
</td>
<td><i>Det uppstod ett fel när din begäran bearbetades.
      Undantagsutskrift är inaktiverat som standard av säkerhetsskäl</code></i>
</tr>
</table>
