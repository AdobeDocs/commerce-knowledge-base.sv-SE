---
title: Kan inte komma åt Adobe Commerce på molninfrastrukturens gränssnitt
description: Den här artikeln innehåller lösningar på problemet där du inte kan logga in på Adobe Commerce i användargränssnittet för molninfrastruktur och få felmeddelandet"403".
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: 3d3d2da45d164efbbbaf8c878967caf83f845a59
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Kan inte komma åt Adobe Commerce på molninfrastrukturens gränssnitt

Den här artikeln innehåller lösningar på problemet där du inte kan logga in på Adobe Commerce i användargränssnittet för molninfrastruktur och få felmeddelandet *403*.

## Problem

När du försöker logga in på ditt Adobe Commerce i molninfrastruktursgränssnitt för första gången visas ett *403: miljöåtkomst nekad* -fel. Det här felet kan uppstå om du går till molnets URL-adress för första gången läser in huvudgrenen och du kanske inte har tillgång till den grenen.

## Lösning

Om du får ett 403-fel första gången du öppnar URL:en kontrollerar du att du har en roll i huvudgrenen.

1. С till licensägaren eller en superanvändare i projektet och se till att de gett dig åtkomst som en **användare på miljönivå**, vilket även beskrivs i [Cloud-projekt > Hantera användare från molnkonsolen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-cloud-console) i vår utvecklardokumentation.

   Om du bara har en tillämplig roll i en viss gren måste du gå till URL:en för den grenen, t.ex.
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   Nästa gång du öppnar huvudwebbadressen används den senaste miljön som standard.

1. Om du fortfarande inte kan logga in kontaktar du с licensägaren eller en superanvändare i projektet och ser till att de gett dig åtkomst som en **projektanvändare**, vilket beskrivs i [Cloud-projekt > Lägg till en användare i projektet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-a-user-to-the-project) i vår utvecklardokumentation.
1. Om felet kvarstår [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
