---
title: 'SQL-frågor: FÖRKLARA kostnadsfel'
description: Den här artikeln innehåller lösningar på kostnadsfel i EXPLAIN när misslyckade SQL-frågor körs. PostgreSQL använder något som kallas [kommandot EXPLAIN](https://www.postgresql.org/docs/9.5/static/using-explain.html) för att fastställa kostnaden för SQL-frågor. Vi har skapat SQL Report Builder för att även använda det här kommandot, vilket innebär att om kostnaden anses vara för hög - mängden resurser som krävs för att köra frågan överskrider våra tröskelvärden - kommer frågan inte att köras och ett EXPLAIN-meddelande visas.
exl-id: 6f6df66a-665e-46a8-ad4c-842a0270c4eb
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# SQL-frågor: FÖRKLARA kostnadsfel

Den här artikeln innehåller lösningar på kostnadsfel i EXPLAIN när misslyckade SQL-frågor körs. PostgreSQL använder något som kallas [EXPLAIN-kommandot](https://www.postgresql.org/docs/9.5/static/using-explain.html) för att fastställa kostnaden för SQL-frågor. Vi har skapat SQL Report Builder för att även använda det här kommandot, vilket innebär att om kostnaden anses vara för hög - mängden resurser som krävs för att köra frågan överskrider våra tröskelvärden - kommer frågan inte att köras och ett EXPLAIN-meddelande visas.

Det finns några anledningar till att det här kan hända. Här är de meddelanden du kan få, vad de betyder och hur du felsöker dem.

## Det gick inte att köra frågan. Kostnadsvärdet \[xxx\] för EXPLAIN är för högt för att köra den här frågan.

Om det här meddelandet visas innebär det att frågan ansågs för dyr för att köras. Vi har två rekommendationer för den här situationen: en är att ta bort ORDER BY-klausuler från din fråga, eftersom de är kostsamma operationer. Det andra är att följa tipsen i vår [optimeringsartikel](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/optimizing-your-sql-queries.html?lang=sv-SE) för att justera din fråga.

## Det gick inte att köra frågan. Frågan returnerar \[xxx\] rader, vilket överskrider gränsen på 10 000

I det här fallet överskrider det möjliga antalet resultat det angivna maxvärdet för SQL Report Builder. Du kan minska antalet resultat på flera olika sätt:

* Försök lägga till filter i frågan.
* Använd LIMIT om du kan. Vissa tabeller har ett stort antal rader och om du begränsar resultatet kan du ligga under radgränsen.

## Det går inte att analysera EXPLAIN-svaret.

Hoppsan. Det här meddelandet betyder vanligtvis att något antagligen gick fel hos oss. Om felet kvarstår kontaktar du supporten.
