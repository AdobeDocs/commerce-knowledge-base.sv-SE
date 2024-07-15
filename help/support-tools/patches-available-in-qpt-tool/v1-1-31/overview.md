---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.31.
exl-id: 0d93619e-0ae6-4dba-9b76-8aeb026c456d
feature: Tools and External Services
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.31

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.31.

QPT v1.1.31 innehåller följande patchar:

1. **ACSD-50817**: Optimerar cron-jobb `sales_clean_quotes` så att det körs snabbare genom att lägga till ett sammansatt index på `store_id` - och `updated_at` -kolumner i citattabellen.
1. **ACSD-50345**: Korrigerar problemet där: [!DNL Google reCAPTCHA v2] inte läses in igen efter att en misslyckad betalning har skickats, [!DNL Google reCAPTCHA v3 Invisible] inte fungerar i utcheckning och ordningen inte kan placeras, och [!UICONTROL PlaceOrder]-händelsen utlöstes inte.
1. **ACSD-49392**: Korrigerar problemet där orderstatusen ändras till stängd efter en partiell återbetalning för en paketerad produkt.
1. **ACSD-51036**: Korrigerar problemet där konkurrensvillkor under samtidiga REST API-anrop resulterar i en överskrivning av leveransstatusinformation i tabellen [!UICONTROL Items Ordered].
1. **ACSD-50858**: Korrigerar problemet där en kupong felaktigt markerats som använd efter en misslyckad kortbetalning.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
