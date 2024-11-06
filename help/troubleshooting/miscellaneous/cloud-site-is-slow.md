---
title: Molnwebbplatsen är långsam
description: I den här artikeln ges rekommendationer om hur du kan göra din Adobe Commerce-webbplats på molninfrastrukturen bättre under belastad trafik och hur du kan minska belastningen.
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---

# Molnwebbplatsen är långsam

I den här artikeln ges rekommendationer om hur du kan göra din Adobe Commerce-webbplats på molninfrastrukturen bättre under belastad trafik och hur du kan minska belastningen.

## Berörda versioner och utgåvor

* Adobe Commerce om molninfrastruktur, alla versioner

## Problem

<u>Steg som ska återskapas</u>

1. Besök Adobe Commerce store.
1. Bläddra bland en kategorisida.
1. Lägg en produkt i kundvagnen.

<u>Förväntat resultat</u>

Webbplatsen är responsiv och det går snabbt att lägga en produkt i kundvagnen.

<u>Faktiskt resultat</u>

Webbplatsen är långsam eller så är kategorisidorna snabba men kundvagnssidan är långsam.

## Felsökning av steg och lösningar

Följ de här stegen för att spåra orsaken till den långsamma prestandan och åtgärda den. Du kan växla det första och det andra steget, men du kan bara fortsätta med att blockera IP-adresser om optimeringen av cacheinställningarna inte hjälper.

1. Kontrollera cacheträffhastigheten för sidor med hög trafik och minska mängden data som uppdateras mycket.
1. Kontrollera den totala träfffrekvensen för platscachen och verifiera den allmänna cachen/snabbkonfigurationen.
1. Identifiera de webbklienter som orsakar den höga serverbelastningen och blockera IP:n som orsakar den höga belastningen.

I följande stycken finns mer information för varje steg.

### Steg 1: Kontrollera cacheträffhastigheten för sidor med hög trafik

Det första steget till att åtgärda en webbplats som störs av stor trafik är att se till att sidor med störst trafik, som butikens hemsida och kategorisidor på den översta nivån cachelagras korrekt.

Du kan ta reda på cacheminnets träfffrekvenser för de här sidorna genom att granska `X-Cache` HTTP-rubriker med cURL, vilket beskrivs i [Kontrollera cacheminnet med cURL](https://docs.fastly.com/guides/debugging/checking-cache#using-curl) i Snabbdokumentation. Du kan också kontrollera samma rubriker på nätverksfliken i utvecklarverktygsfältet i din favoritwebbläsare.

I allmänhet respekterar svarshuvuden som kommer från programmet, men om alla sidhuvuden är inställda på &quot;cachelagra inte&quot; och för sidan &quot;förfaller tidigare&quot; kan du inte cachelagra sidan.

>[!WARNING]
>
>Observera att Snabb ändrar svarshuvuden, så om du kontrollerar huvud-URL:en med cURL eller webbläsaren visas inte nödvändigtvis vilka huvuden som skickas av programmet. Det är vanligt att Fastly själv svarar på webbläsare med rubriker utan cache, men att själva webbprogrammet tillåter cachelagring och att Fast cachelagrar objektet ordentligt. Därför kommer rubrikinformationen &quot;cache-control&quot; och &quot;pragma&quot; inte att vara användbar i det här fallet.

#### Felsökning för sidor med hög trafik

Om indexsidan har en låg träfffrekvens kan du åtgärda den genom att minska mängden data som är starkt uppdaterade på sidan.

### Steg 2: Kontrollera den totala träfffrekvensen för platscache

Så här kontrollerar du den totala cacheminnesträffhastigheten:

1. [Få snabbt inloggningsuppgifter](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration) för din Adobe Commerce i molninfrastrukturmiljö.
1. Kör följande Linux/macOS cURL-kommando för att kontrollera träffhastigheten för din webbplats under de senaste 30 minuterna, och ersätt och med värdena för dina snabbinloggningsuppgifter:

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   Du kan också kontrollera tidigare träfffrekvenser under den sista dagen eller månaden genom att ändra frågealternativet för tidsintervall från `?by=minute` till `?by=hour` eller `?by=day`. Mer information om hur du får status för snabbcache finns i [Frågealternativ](https://docs.fastly.com/api/stats#Query) i dokumentationen Snabbt.

   Alternativet `| json_pp` skriver ut JSON-svarsutdata med verktyget `json_pp`. Om du får ett_&#39;json\_pp not found&#39;_-fel installerar du verktyget `json_pp` eller använder ett annat kommandoradsverktyg för JSON-utskrift. Du kan också ta bort parametern `| json_pp` och köra kommandot igen. JSON-svarsutdata är inte formaterade, men du kan rensa upp det genom en JSON-finjustering.

En träfffrekvens över 0,90 eller 90 % anger att helsidescachen fungerar.

En träfffrekvens under 0,85 eller 85 % kan tyda på ett platskonfigurationsproblem, eller så har du ett tillägg från tredje part installerat som inte tillåter att innehållet cachelagras.

#### Felsökning av den totala träfffrekvensen för cache

1. Identifiera när träfffrekvensen började sjunka med hjälp av träffstatistik per timme och dag. Om träfffrekvensen plötsligt skulle minska vid samma tidpunkt som du distribuerade en ändring till din webbplats bör du överväga att återställa ändringen tills webbplatsinläsningen går ner.
1. Kontrollera konfigurationen i Commerce Admin, under **Lagrar** > **Konfiguration** > Avancerat > **System** > **Helsidescache**. Kontrollera att värdet **TTL för publikt innehåll** inte är för lågt.
1. Kontrollera att du har [överfört VCL-kodfragment](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
1. Om du använder anpassade VCL-kodfragment kan du felsöka dem för korrekt användning av åtgärderna &quot;pass&quot; eller &quot;pipe&quot;: de bör användas med försiktighet och i alla lägen med något slags tillstånd. Mer tips finns i [Anpassade snabbvalsbaserade VCL-kodfragment](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) i utvecklardokumentationen.

### Steg 3: Identifiera de webbplatser som orsakar hög serverbelastning

Du kan använda någon av följande metoder för att få information om IP-adresserna som har åtkomst till din Adobe Commerce-butik.

* Kontrollera HTTP-åtkomstloggarna via en SSH-session.
* Kontakta Adobe Commerce support för att få en lista över IP-adresser som orsakar hög belastning på webbplatsen.

#### Kontrollera HTTP-åtkomstloggarna

Om du vill visa platsens åtkomstlogg kör du följande kommando från den lokala utvecklingsmiljön:

```bash
magento-cloud log access
```

Visa fler rader med

```bash
--lines
```

alternativ, till exempel:

```bash
magento-cloud log access --lines=500
```

Du kan visa den här loggen och kontrollera om en stor del av begäranden kommer från en viss IP-adress. Ett annat sätt är att använda `awk`, `sort` och `uniq` för att automatiskt räkna de oftast förekommande IP-adresserna i loggen, enligt följande:

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

Om

```bash
magento-cloud log
```

kommandot fungerar inte, du kan ansluta till fjärrservern med SSH och kontrollera loggfilen på `/var/log/access.log`

När du har identifierat IP-adresserna som orsakar hög serverbelastning kan du blockera dem genom att konfigurera ett IP-blockeringslista från Commerce Admin-panelen, under **Lager** > **Konfiguration** > AVANCERAT > **System** > **Fullständig sidcache** > **Snabbkonfiguration** > **Blockera**.

Om du inte kan komma åt din administratör på grund av stor belastning kan du använda API:t Fastly för att konfigurera blockeringsreglerna:

1. Skapa åtkomstkontrollistan enligt beskrivningen i [Arbeta med åtkomstkontrollistor med API:t ](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api) Snabbt.
1. I avsnittet `recv` skapar du ett VCL-fragment med följande innehåll, som har ersatt ACL\_NAME\_GOES\_HERE med namnet på den åtkomstkontrollista som skapades i föregående steg:

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

Mer information om att blockera IP-adresser finns i guiden för [Snabb Adobe Commerce-modul](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) i GitHub.
