---
title: 'Det gick inte att komma åt Adobe Commerce i molnet: 403 Otillåten eller 404 Inte hittad vid distribution'
description: 'I den här artikeln beskrivs hur du löser problemet med misslyckade distribueringsfel i Adobe Commerce om molninfrastruktur på ungefär följande sätt:'
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# Det gick inte att komma åt Adobe Commerce i molnet: 403 Otillåten eller 404 Inte hittad vid distribution

I den här artikeln beskrivs hur du löser problemet med misslyckade distribueringsfel i Adobe Commerce om molninfrastruktur på ungefär följande sätt:

&quot;*Det gick inte att komma åt https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL: HTTP/1.1 403 Forbidden* &quot;. Eller så gick det inte att hämta filen *https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip (HTTP/1.1 404 Hittades inte)*.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x och 2.4.x

## Problem

Felmeddelande vid distribution som anger att repo-URL:en inte kunde nås.

<u>Steg som ska återskapas</u>

Utlös distributionen manuellt eller genom att utföra en sammanslagning, push eller synkronisering av din miljö.

<u>Faktiskt resultat</u>

Driftsättningen fastnar. I distributionsfelloggen i projektanvändargränssnittet visas ett felmeddelande som liknar följande:

*&quot;Det gick inte att komma åt https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL: HTTP/1.1 \[403 Forbidden eller 404 Hittades inte\]&quot;*.

(Klicka på ikonen &quot;Fel&quot; i projektgränssnittet för att visa loggen.)

<u>Förväntat resultat</u>

Distributionen har slutförts.

## Orsak

Felet orsakas av att auktoriseringsnycklarna (åtkomstnycklarna) inte är giltiga, inte angivna eller inte har angetts korrekt.

Några orsaker till att nycklarna inte är giltiga är:

* Du genererade nycklarna med ditt delade konto.
* Licensen har tidigare återkallats på grund av betalningsproblem.

>[!NOTE]
>
>Om du upptäcker att detta beror på ett fakturerings- eller annullerat avtalsproblem kan du kontakta ditt kontoteam på Adobe för att få hjälp med att lösa problemet. När licensen har återaktiverats återställs din support och dina distributionsrättigheter.

## Lösning

Gör så här för att lösa problemet med auktoriseringsnycklarna (se avsnitten nedan för mer information om varje steg):

1. Hämta giltiga auktoriseringsnycklar (hoppa över detta om du är helt säker på att din nyckel är giltig).
1. Lägg till nyckelvärdet i variabeln `env:COMPOSER_AUTH` (eller se till att rätt värde finns) och kontrollera om nycklarna anges konsekvent i variabeln på projektnivå och miljönivå samt i filen `auth.json` (om den finns) i projektroten.
1. Uppdatera eller ta bort `auth.json`, så att det finns en plats där nyckeln är konfigurerad, om värdena för auktoriseringsnycklar inte har angetts eller har ett annat värde.

### 1. Skaffa giltiga auktoriseringsnycklar

Om du använder nycklarna som skapats med det delade kontot måste du kontakta den Adobe Commerce-licensägare som ger dig åtkomst och begära att de genererar nycklarna åt dig.

Om din licens har återkallats tidigare på grund av betalningsproblem och du har löst problemen och din licens har förnyats, måste du [generera de nya autentiseringsnycklarna](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html?lang=sv-SE).

### 2. Lägg till nyckelvärdet i variabeln env:COMPOSER\_AUTH och kontrollera om samma nycklar anges i auth.json

Se instruktionerna och relaterad information i [Förbered ditt befintliga system](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/project/overview) och [Lägg till autentiseringsnycklar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/project/overview) i utvecklardokumentationen.

### 3. Uppdatera eller ta bort auth.json

Här följer en stegvis beskrivning av hur du uppdaterar dina auktoriseringsnycklar:

1. Logga in på den dator som har din Adobe Commerce på SSH-nycklar för molninfrastruktur.
1. Logga in på ditt projekt: `magento-cloud login`
1. Skapa en gren för att uppdatera koden (i följande exempel skapas grennamnet `auth` från den primära grenen):     `magento-cloud environment:branch auth master`
1. Byt till projektets rotkatalog.
1. Valfritt: Ta bort `auth.json` om du vill och fortsätt till [steg 9](#step9).
1. Öppna `auth.json` i en textredigerare.

   ```json
              {
                "http-basic":  {
                    "repo.magento.com": {
                        "username": "<public_key>",
                        "password": "<private_key>"
                        }
                      }
                    }
   ```

1. Lägg till rätt autentiseringsnycklar.
1. Spara ändringarna och avsluta textredigeraren.
1. Genomför och sammanfoga dina ändringar:

   `git add -A`

   `git commit -m "<message>"`

   `git push origin master`
1. Vänta på att projektet ska distribueras.
