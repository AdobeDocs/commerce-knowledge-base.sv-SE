---
title: Felsökningsguide för verktyget Adobe Commerce Security Scan
description: Lär dig hur du felsöker de olika problemen med verktyget för säkerhetsgenomsökning för Adobe Commerce och Magento Open Source.
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: c6e338fb33477ab107fe4de382b485339b57275a
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 0%

---

# Felsökningsguide för verktyget Adobe Commerce Security Scan

Lär dig hur du felsöker de olika problemen med verktyget för säkerhetsgenomsökning för Adobe Commerce och Magento Open Source.

## Problem: Det gick inte att skicka webbplatsen

För säkerhetsgenomsökningsverktyget måste du bevisa att du är ägare till din webbplats innan domänen kan läggas till i säkerhetsgenomsökningsverktyget. Du kan göra detta genom att lägga till en bekräftelsekod på webbplatsen med en HTML-kommentar eller taggen `<meta>`. HTML-kommentaren ska placeras inuti taggen `<body>`, t.ex. i sidfotsavsnittet. Taggen `<meta>` ska placeras inuti sidans `<head>`-avsnitt.

Ett vanligt problem som handlare ställs inför uppstår när verktyget för säkerhetsgenomsökning inte kan bekräfta handlarens ägarskap på webbplatsen.

Om du får ett fel och inte kan skicka din webbplats för genomsökningen kan du läsa felmeddelandet [när du lägger till webbplatser i felsökningsartikeln för säkerhetsgenomsökning](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md) i vår kunskapsbas för support.

## Problem: Tomma rapporter som har genererats av verktyget Säkerhetskontroll

Du får tomma genomsökningsrapporter från verktyget för säkerhetsgenomsökning eller får rapporter som bara innehåller ett fel, t.ex. *Säkerhetsverktyget kunde inte nå bas-URL:en* eller *Magento-installationen finns inte på den angivna URL:en*.

### Lösning

1. Kontrollera att 52.87.98.44, 34.196.167.176 och 3.218.25.102 IP-adresser inte blockeras vid 80- och 443-portar.
1. Kontrollera den skickade URL:en för omdirigeringar (t.ex. omdirigeras `https://mystore.com` till `https://www.mystore.com` eller vice versa eller omdirigeras till andra domännamn).
1. Undersök åtkomstloggar för WAF-/webbservrar för nekade/ej fullgjorda begäranden. HTTP 403 `Forbidden` och HTTP 500 `Internal server error` är de vanligaste serversvaren som orsakar tom rapportgenerering. Här är ett exempel på den bekräftelsekod som blockerar begäranden från användaragenter:

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

Du kan också se [Rapporten från verktyget för säkerhetsgenomsökning är tom](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md) i vår kunskapsbas för support för mer information.

## Problem: Säkerhetsproblemet har lösts men är fortfarande sårbart vid skanning

Du löste ett säkerhetsproblem och väntar på att säkerhetsgenomsökningen ska visa att du inte längre är sårbar för det nyligen lösta problemet. I stället ser du att rapporten som genererats av säkerhetsgenomsökningen fortfarande rapporterar att du är sårbar för säkerhetsproblemet.

### Orsak

Metadata för molninstanser samlas endast in för `active` och `live` Cloud-projekt och är INTE en realtidsprocess.

Skriptet för statistikinsamling körs en gång om dagen och verktyget för säkerhetsgenomsökning måste hämta nya data senare.

Förväntad fördröjning i synkroniseringscykeln är upp till en vecka och tar minst 24 timmar.

Följande statusvärden kan visas vid kontroller:

1. **Steg**: Säkerhetsgenomsökningsverktyget har sökt igenom dina uppdaterade data och godkänt ändringarna.
1. **Okänd**: Verktyget för säkerhetsgenomsökning har inga data om din domän än; vänta på nästa synkroniseringscykel.
1. **Misslyckades**: Om statusen inte fungerar måste du åtgärda problemet (aktivera 2FA, ändra administratörs-URL osv.) och vänta på nästa synkroniseringscykel.

Om 24 timmar har gått sedan ändringarna gjordes för instansen och de inte återspeglas i säkerhetsgenomsökningsrapporten, kan du [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Ange butiks-URL när du skickar biljetten.

## Misslyckad BotNet Suspect

Du får ett meddelande om felet &quot;BotNet Suspect&quot;.

### Orsak

1. Butikens domännamn introducerades i en lista över potentiella BotNet-deltagare redan 2019, och administratörspanelen, hämtningsfunktionen eller RSS-funktionen exponerades offentligt, och/eller dess URL har nämnts i CC-gallringsforumen.
1. Varningen kan orsakas av tecken på butikskompromiss och/eller skadlig kod, som JavaScript på sidan.
1. Det behöver inte nödvändigtvis vara en pågående fråga. Om butiken har komprometterats tidigare kan värdnamnet fortfarande flyta runt på den mörka webben som namnet &#39;offer&#39;.
1. Den kan också orsakas av en systemkompromiss (på operativsystemsnivå), inte av Adobe Commerce.

### Lösning

1. Kontrollera om det finns nyligen skapade SSH-konton, ändringar i filsystemet osv.
1. Genomför en säkerhetsgranskning.
1. Kontrollera Adobe Commerce-versionen och uppgraderingen, särskilt om den fortfarande kör Magento 1, som inte stöds längre.
1. Om problemet kvarstår [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och anger butikens URL.

## Problem: Komprometterad inmatningsfel

Du får ett felmeddelande om felet &quot;Kompromissinmatning&quot;.

### Lösning

1. Granska skripten som anges i rapporten för verktyget för säkerhetsgenomsökning.
1. Granska startsidans källtext för infogade skript.
1. Granska ändringar av systemkonfigurationen, särskilt anpassade `HTML head`- och `Miscellaneous HTML`-värden i `footer`-avsnittsvärden.
1. Utför kodgranskning och databasgranskning för att se om det finns några okända ändringar och tecken på inmatad skadlig kod.

Om inget av ovanstående hjälper, [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och anger butiks-URL:en och felmeddelandet från rapporten.

## Vanliga frågor

### Kommer säkerhetsgenomsökningen att påverka prestandan på min webbplats?

Nej. Med säkerhetsgenomsökningen kan du göra alla förfrågningar en i taget som en enskild användare. På grund av detta bör säkerhetsgenomsökningen inte påverka webbplatsens prestanda.

### Hur länge har Adobe Commerce rapporter om säkerhetsgenomsökning?

Du kan generera de 10 föregående rapporterna från din sida. Kontakta Adobe Commerce support om det krävs äldre rapporter.

### Vilken information behövs när du skickar in en supportanmälan?

Ange domännamnet exakt som det skickas för [säkerhetsgenomsökningen](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26357), MAGEID och Creative_ID för molnet. Observera att Creative Cloud Project_ID inte krävs för Adobe Commerce lokalt.

### Vad händer om jag tar bort min butik från skanning av skanningsverktyg?

Om du tar bort arkivöverföringen tas alla relaterade data, inklusive genomsökningsrapporter, bort. Åtgärden kan inte ångras. Om du skickar arkivdomänen efter att den tagits bort skapas en NY överföring.
