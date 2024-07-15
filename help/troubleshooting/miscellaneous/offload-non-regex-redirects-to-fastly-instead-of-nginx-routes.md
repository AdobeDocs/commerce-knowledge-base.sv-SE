---
title: Avlasta icke-regex-omdirigeringar till Fast istället för Nginx (rutter)
description: I det här avsnittet ges förslag på en lösning på ett typiskt prestandaproblem som kan uppstå när du avlastar icke-regex omdirigeras till Fastly i stället för Nginx i Adobe Commerce i molninfrastruktur.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Avlasta icke-regex-omdirigeringar till Fast istället för Nginx (rutter)

I det här avsnittet ges förslag på en lösning på ett typiskt prestandaproblem som kan uppstå när du avlastar icke-regex omdirigeras till Fastly i stället för Nginx i Adobe Commerce i molninfrastruktur.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen (alla versioner) `Master/Production/Staging`-miljöer utnyttjar snabbt

## Problem

I Adobe Commerce i molninfrastruktur kan ett stort antal omdirigeringar/omskrivningar som inte är regex inte utföras i Nginx-lagret, vilket kan leda till prestandaproblem.

## Orsak

Filen `routes.yaml` i katalogen `.magento/routes.yaml` definierar vägar för din Adobe Commerce i molninfrastruktur.

Om storleken på din `routes.yaml`-fil är 32 kB eller större bör du avlasta icke-regex-omdirigeringar/omskrivningar till Fast.

Det här Nginx-lagret kan inte hantera ett stort antal omdirigeringar/omskrivningar som inte är regex, eftersom prestandaproblem då uppstår.

## Lösning

Lösningen är att avlasta de icke-regex-omdirigeringar till Fastly istället. Skapa en allmän felsökväg som du kan dirigera om till Snabbt.

I följande steg beskrivs hur du placerar omdirigeringar på Snabb i stället för Nginx.

1. Skapa en Edge-ordlista.

   Först kan du använda [VCL-fragment i Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) för att definiera en kantordlista. Detta kommer att innehålla omdirigeringarna.

   Några kavaater till detta:

   * Regex kan inte användas i ordlisteposter. Det är bara en exakt träff. Mer information om de här begränsningarna finns i [Fastly&#39;s docs on edge dictionary limits](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * Har en gräns på 1 000 poster i ett och samma lexikon. Du kan snabbt utöka den här gränsen, men det leder till den tredje kavatten.
   * Varje gång du uppdaterar posterna och distribuerar den uppdaterade VCL-listan till alla noder ökar den geometriska belastningstiden med expanderande ordlistor, vilket innebär att en 2 000-postordlista läses in 3x-4x långsammare än en 1 000-postordlista. Men det är bara ett problem när du distribuerar VCL (uppdaterar ordlistan eller ändrar VCL-funktionskoden).

     Det påverkar inte den tid det tar att snabbt behandla en begäran; det påverkar bara hur lång tid det tar att snabbt skicka ut en ny konfiguration.

     I allmänhet tar konfigurationsändringar några sekunder i genomsnitt, vanligtvis inte mer än 5-10 sekunder. Så en tvåfaldig ökning av ordlisteobjekt tar upp till 30 sekunder att få igång konfigurationen. En ökning med fyra gånger skulle ta närmare 2 minuter. Detta leder till den fjärde grottan.

   * Det finns en ganska hård gräns på 10 000 poster i en kantordlista.

   Vi rekommenderar starkt att du konsoliderar din omdirigeringslista. Du kan använda flera ordlistor, men tänk bara på att det tar flera minuter att fylla i din VCL-lista över Fast.

1. Jämför URL:en med ordlistan/ordlistorna.

   När URL-sökningen görs görs jämförelsen för att tillämpa den anpassade felkoden om en matchning hittas.

   Använd ett annat VCL-fragment för att lägga till något som följande i `vcl_recv`:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Här kontrollerar vi om URL:en finns i tabellposten. Om så är fallet anropar vi ett internt fast-fel och skickar omdirigerings-URL:en från tabellen till felet.

1. Hantera omdirigeringen.

   När en matchning hittas utförs åtgärden som är definierad för `obj.status`, i det här fallet en permanent flyttomdirigering om 301.

   Använd ett sista utdrag i `vcl_error` för att skicka tillbaka 301-felkoder till klienten:

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Med det här blocket kontrollerar vi om felkoden som skickas från `vcl_recv` matchar, och i så fall anger vi platsen till det felmeddelande som skickas, ändrar statuskoden till 301 och meddelandet till&quot;Flyttad permanent&quot;. Då bör svaret vara klart att skickas tillbaka till klienten.

### Stage Service

>[!WARNING]
>
>Om du vill prova alla dessa steg bör du konfigurera en mellanlagringsmiljö för Adobe Commerce. På så sätt kan du köra tester mot tjänsten Fastly för att säkerställa att allt fungerar som du tänkt dig.

Om du inte vill köra en mellanlagringsmiljö från Adobe Commerce, men vill se hur omdirigeringarna skulle se ut, kan du konfigurera ett mellanlagringskonto direkt på Fastly.

## Relaterad läsning

* [Snabbt VCL-referens](https://docs.fastly.com/vcl/)
* [Konfigurera vägar](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) i utvecklardokumentationen.
* [Konfigurera snabbt](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) i utvecklardokumentationen.
* [VCL-informationsblad för reguljära uttryck](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) i vår utvecklardokumentation.
