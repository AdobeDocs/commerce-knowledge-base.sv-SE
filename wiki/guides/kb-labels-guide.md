---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---
# KB Labels Guide

Det här dokumentet innehåller riktlinjer för hur du lägger till etiketter i artiklar i Adobe Commerce Support Knowledge Base.
Etiketter (kallas även taggar) förbättrar sökningen i [Adobe Commerce Support Knowledge Base](https://support.magento.com/hc/en-us).
Etiketter läggs till i fältet&quot;Etiketter&quot; i metadataavsnittet i en artikelfil, avgränsade med kommatecken, utan mellanrum mellan kommatecken och nästa etikett.
Mer information finns i [./../.github/CONTRIBUTING.md#metadata].

## Allmänna bestämmelser

Lägg till följande etiketttyper för varje artikel:

* Etikett(er) för produkt(er). (obligatoriskt)
* Etikett(er) för versioner som påverkas. (obligatoriskt, utom artiklar som rör allmänt stöd)
* Etikett för innehållstyp. (obligatoriskt)
* Etiketter för större teknikkomponent.(om tillämpligt)
* Etiketter för den process/funktion som felsöks/beskrivs. (om tillämpligt)
* Etiketter för den utgåva som åtgärdas/beskrivs. (om tillämpligt)

Se avsnitten nedan för detaljerade rekommendationer om hur du definierar etiketter för var och en av dessa etiketttyper.

## Etiketter för produkter

<table>
<tbody>
  <tr>
    <th>Produktnamn</th>
    <th>Etikett</th>
  </tr>
  <tr>
    <td>Adobe Commerce (alla distributionsmetoder) </td>
    <td>
    "Adobe Commerce,molninfrastruktur,lokal"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce i molninfrastruktur</td>
    <td>
      "Adobe Commerce,molninfrastruktur"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce lokalt</td>
    <td>"Adobe Commerce, lokalt"</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence (MBI)</td>
    <td>
        "Magento Business Intelligence,MBI"
    </td>
  </tr>
   <tr>
    <td>Magento Open Source</td>
    <td>
        "Magento Open Source"
    </td>
  </tr>
  <tr>
    <td>B2B för Adobe Commerce</td>
    <td>"B2B"</td>
  </tr>
  <tr>
    <td>PWA för Adobe Commerce</td>
    <td>"PWA"</td>
  </tr>
  <tr>
    <td>Venia storefront-projektet</td>
    <td>’Venia’</td>
  </tr>
  <tr>
    <td>QPT-verktyg</td>
    <td>"Verktyget Kvalitetspatchar,QPT-patchar"</td>
  </tr>
  </tbody>
</table>

## Etiketter för produktversioner

* Lägg till en separat etikett för varje version av Adobe Commerce. Exempel: &quot;2.3.7&quot;
* Lägg inte till etiketter för intervall.
Det vill säga, om 2.3.0-2.3.5 påverkas, lägg till: &quot;2.3.0,2.3.1,2.3.2,2.3.2-p2,2.3.3,2.3.3-p1,2.3.4,2.3.4-p2,2.3.5-p1,2.3.5-p2&quot;
NOT &quot;2.3.0-2.3.5&quot;
* Lägg inte till etiketter med .x. Exempel: &quot;2.3.x&quot;

## Etiketter för innehållstyp (baserat på kategori)

<table>
  <tbody>
    <tr>
      <th>Kategori</th>
      <th>Etikett</th>
    </tr>
    <tr>
      <td>Bästa praxis</td>
      <td>"bästa praxis" (inte"bästa praxis" eller"bästa praxis")</td>
    </tr>
    <tr>
      <td>
        Felsökning
      </td>
      <td>
      felsökning
      </td>
    </tr>
    <tr>
      <td>Så här gör du</td>
      <td>"how to"</td>
    </tr>
    <tr>
      <td>Vanliga frågor</td>
      <td >"Frågor och svar"</td>
    </tr>
  </tbody>
</table>

## Etiketter för större tekniska komponenter

* Använd skiftläge enligt komponentens officiella namn.
* Använd inte synonymer, en etikett för en komponent.
* En ordetikett är att föredra, men om komponentnamnet innehåller flera ord använder du flera ord. Lägg inte till några felbeskrivningar. Lägg alltså&quot;Elasticsearch&quot; i stället för&quot;Elasticsearch problem&quot;.
* Om innehållet endast är relevant för en viss version av komponenten lägger du till en etikett med namnet + version.\
  Exempel: &quot;Elasticsearch 5&quot;. Om det är relevant för flera olika versioner lägger du till flera etiketter av den här typen. Exempel: &quot;Elasticsearch 5&quot;, &quot;Elasticsearch 6&quot;. Om det är relevant använder du&quot;x&quot; för flera versioner. Exempel: &quot;Elasticsearch 2.x&quot;

Exempel:

* &quot;Elasticsearch&quot;
* &quot;New Relic&quot;
* &quot;Webbinstallationsguiden&quot;

## Etiketter för den process/funktion som felsöks/beskrivs

* Använd gemener, med undantag för riktiga substantiv.
* Använd inte synonymer, en etikett för en enhet.
* En ordetikett är att föredra. Lägg inte till någon problembeskrivning. Det vill säga lägg till &quot;database&quot; i stället för &quot;database crashes&quot;.

Exempel: 

* &quot;database&quot;
* &quot;cron&quot;
* &quot;deployment&quot;
* &quot;massuppdatering&quot;

## Etiketter för den utgåva som åtgärdas/beskrivs

* Använd gemener, med undantag för riktiga substantiv.
* Använd inte synonymer, en etikett för en enhet.
* En ordetikett är att föredra. Konvertera inte felmeddelanden till etiketter.

Exempel:

* &quot;site down&quot;
* &quot;500-fel&quot;
* &quot;fast kron&quot;
