---
title: "Adobe Commerce i molnet: ändra autentiseringsnycklar och omdistribuera"
description: Den här artikeln innehåller anvisningar om hur du distribuerar om Adobe Commerce i molninfrastruktur med olika autentiseringsnycklar. Du kan till exempel ha använt nycklarna för ett annat konto eller så har du använt Magento Open Source i stället för Adobe Commerce nycklar.
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce i molnet: ändra autentiseringsnycklar och återdistribuera

Den här artikeln innehåller anvisningar om hur du distribuerar om Adobe Commerce i molninfrastruktur med olika autentiseringsnycklar. Du kan till exempel ha använt nycklarna för ett annat konto eller så har du använt Magento Open Source i stället för Adobe Commerce nycklar.

Om du använde fel nycklar misslyckas distributionen. Om du vill återställa projektet måste du klona projektet, lägga till rätt nycklar i `auth.json`och flytta ändringen till huvudgrenen.

I den här artikeln antar vi att ditt projekt har en `master` endast förgrening (`master` är standardgrenen när du skapar ett projekt).

Så här återdistribuerar du med rätt autentiseringsnycklar:

1. Logga in på den dator som har din Adobe Commerce på SSH-nycklar för molninfrastruktur.
1. Logga in på projektet:

   ```
   magento-cloud login
   ```

1. Skapa en gren för att uppdatera kod med namnet `auth`:

   ```
   magento-cloud environment:branch auth master
   ```

1. Byt till projektets rotkatalog.
1. Öppna `auth.json` i en textredigerare.

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Lägg till rätt autentiseringsnycklar.
1. Spara ändringarna och avsluta textredigeraren.
1. Genomför och sammanfoga ändringarna.

   ```
   git add -A
   ```

   ```
   git commit -m "<description of change>"
   ```

   ```
   git push origin master
   ```

1. Vänta tills distributionen är klar.

Meddelanden anger om distributionen lyckades. Du kan bekräfta att distributionen lyckades genom att gå till någon av **Miljövägar** visas på skärmen.
