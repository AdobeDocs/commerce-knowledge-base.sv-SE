---
title: Avlastning av icke-[!DNL regex] omdirigeras till [!DNL Fastly] i stället för  [!DNL Nginx] (vägar)
description: Det här avsnittet föreslår en lösning på ett typiskt prestandaproblem som kan uppstå när du avlastar icke-[!DNL regex] omdirigerar till  [!DNL Fastly] i stället för  [!DNL Nginx]  i Adobe Commerce om molninfrastruktur.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Avlastning av icke-[!DNL regex] omdirigeras till [!DNL Fastly] i stället för [!DNL Nginx] (vägar)

Det här avsnittet föreslår en lösning på ett typiskt prestandaproblem som kan uppstå när du avlastar icke-[!DNL regex] omdirigerar till [!DNL Fastly] i stället för [!DNL Nginx] i Adobe Commerce om molninfrastruktur.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur (alla versioner) `Master/Production/Staging`-miljöer som utnyttjar [!DNL Fastly]

## Problem

I Adobe Commerce i molninfrastruktur kan ett stort antal omdirigeringar/omskrivningar som inte är [!DNL regex] inte utföras i [!DNL Nginx] -lagret, vilket kan orsaka prestandaproblem.

## Orsak

Filen `routes.yaml` i katalogen `.magento/routes.yaml` definierar vägar för din Adobe Commerce i molninfrastruktur.

Om storleken på din `routes.yaml`-fil är 32 kB eller större bör du avlasta icke-[!DNL regex] omdirigeringar/omskrivningar till [!DNL Fastly].

Det här [!DNL Nginx]-lagret kan inte hantera ett stort antal omdirigeringar/omskrivningar som inte är [!DNL regex], annars kan prestandaproblem uppstå.

## Lösning

Lösningen är att avlasta de icke-[!DNL regex] omdirigeringarna till [!DNL Fastly] i stället. Skapa en allmän felsökväg att omdirigera till [!DNL Fastly].

I följande steg beskrivs hur du placerar omdirigeringar på [!DNL Fastly] i stället för [!DNL Nginx].

1. Skapa en Edge-ordlista.

   Först kan du använda [[!DNL VCL] kodfragment i Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) för att definiera en kantordlista. Detta kommer att innehålla omdirigeringarna.

   Några kavaater till detta:

   * [!DNL Fastly] kan inte göra [!DNL regex] för ordlisteposter. Det är bara en exakt träff. Mer information om de här begränsningarna finns i [[!DNL Fastly]s dokument om begränsningar för kantordlistor ](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * [!DNL Fastly] har en gräns på 1 000 poster i en enda ordlista. [!DNL Fastly] kan utöka den här gränsen, men det leder till den tredje grottan.
   * Varje gång du uppdaterar posterna och distribuerar de uppdaterade [!DNL VCL] till alla noder ökar den geometriska inläsningstiden med expanderande ordlistor, vilket innebär att en 2 000-postordlista läses in 3x-4x långsammare än en 1 000-postordlista. Men det är bara ett problem när du distribuerar [!DNL VCL] (uppdaterar ordlistan eller ändrar [!DNL VCL]-funktionskoden).

     Det påverkar inte den tid det tar [!DNL Fastly] att behandla en begäran. Det påverkar bara hur lång tid det tar [!DNL Fastly] att distribuera en ny konfiguration.

     I allmänhet tar konfigurationsändringar några sekunder i genomsnitt, vanligtvis inte mer än 5-10 sekunder. Så en tvåfaldig ökning av ordlisteobjekt tar upp till 30 sekunder att få igång konfigurationen. En ökning med fyra gånger skulle ta närmare 2 minuter. Detta leder till den fjärde grottan.

   * Det finns en ganska hård gräns på 10 000 poster i en kantordlista.

   Vi rekommenderar starkt att du konsoliderar din omdirigeringslista. Du kan använda flera ordlistor, men tänk bara på att det tar flera minuter att fylla i alla uppdateringar du gör i [!DNL VCL] i [!DNL Fastly].

1. Jämför [!DNL URL] med ordlistan/ordlistorna.

   När [!DNL URL]-sökningen inträffar görs jämförelsen för att tillämpa den anpassade felkoden om en matchning hittas.

   Använd ett annat [!DNL VCL]-fragment för att lägga till något som följande i `vcl_recv`:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Här kontrollerar vi om [!DNL URL] finns i tabellposten. Om det gör det anropar vi ett internt [!DNL Fastly]-fel och skickar omdirigeringen [!DNL URL] från tabellen till det felet.

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
>Om du vill prova alla dessa steg bör du konfigurera en mellanlagringsmiljö för Adobe Commerce. På så sätt kan du köra tester mot tjänsten [!DNL Fastly] för att se till att allt fungerar som du tänkt dig.

Om du inte vill köra en mellanlagringsmiljö från Adobe Commerce, men vill se hur dessa omdirigeringar skulle se ut, kan du konfigurera ett mellanlagringskonto direkt på [!DNL Fastly].

## Relaterad läsning

* [[!DNL Fastly VCL] referens](https://docs.fastly.com/vcl/)
* [Konfigurera vägar](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) i utvecklardokumentationen
* [Konfigurera [!DNL Fastly]](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) i utvecklardokumentationen
* [[!DNL VCL] informationsblad för reguljära uttryck](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) i utvecklardokumentationen
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
