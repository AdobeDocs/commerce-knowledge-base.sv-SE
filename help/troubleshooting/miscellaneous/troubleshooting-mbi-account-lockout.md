---
title: Felsökning av Adobe Commerce Intelligence-kontoutelåsning
description: Den här artikeln innehåller lösningar för Adobe Commerce Intelligence-kontolåsning. Först måste vi se om det är en defekt, ett tillfälligt fel eller något annat. Om du följer stegen nedan kommer du att få tillbaka ditt konto så snabbt som möjligt.
exl-id: 85968257-ba4b-4cfb-a4fa-497b4c5b5aea
feature: Cache, Commerce Intelligence, Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# Felsökning av Adobe Commerce Intelligence-kontoutelåsning

<!--
BOB: Is this in TOC?
-->

Den här artikeln innehåller lösningar för Commerce Intelligence-kontolåsning. Först måste vi se om det är en defekt, ett tillfälligt fel eller något annat. Om du följer stegen nedan kommer du att få tillbaka ditt konto så snabbt som möjligt.

## Verifiera att din e-postadress är korrekt

Kontrollera din e-postadress för att vara säker på att den e-postadress som du försöker använda för att logga in är kopplad till ett befintligt Commerce Intelligence-konto. Du kan behöva be en kontoadministratör bekräfta att det inte finns några stavfel i e-postadressen.

När du har bekräftat att e-postadressen är korrekt försöker du logga in igen med [den här länken](https://dashboard.rjmetrics.com/v2/session/create#/).

## Försök återställa lösenordet

Om du har verifierat att du använder rätt e-postadress kan du försöka med att återställa lösenordet. Du kan använda **Har du glömt?** på inloggningssidan från föregående avsnitt för att utlösa ett e-postmeddelande för återställning av lösenord.

Om du inte ser e-postmeddelandet först måste du titta i skräppostmappen. Ibland kan till och med välavsiktliga e-postmeddelanden förväxlas för skräppost. **Observera att länkarna för temporär åtkomst i dessa e-postmeddelanden bara fungerar en gång!**

Om du fortfarande är utelåst måste du vara säker på att din e-postadress är korrekt och du använder rätt länk från återställningsmeddelandet. Vi rekommenderar att du provar följande **innan du begär en ny återställning och försöker logga in igen:**

* Rensa webbläsarens cache, cookies och sparade lösenord
* Stäng tillfälligt av alla annonsblockerande program

## Dokumentera eventuella fel och kontakta support

>[!NOTE]
>
>Det här steget behövs inte alltid, men om du utför det proaktivt kan det minska den tid det tar att gå fram och tillbaka på en supportförfrågan.

Om du fortfarande inte kan komma åt ditt konto rekommenderar vi att du söker efter fel och skickar in en biljett till vårt supportteam. Hur kan du göra såhär? Genom att öppna utvecklarverktygen i webbläsaren och ta en skärmbild av eventuella fel som visas i konsolen eller i loggfönstret. I GIF nedan öppnar jag utvecklingsverktygen för Google Chrome:

![Öppna Chrome&#39;s utvecklarverktyg.](assets/Opening_Chrome_dev_tools.gif)

I exemplet ovan använde vi den vanligaste metoden (**högerklicka** > **Inspect**) för att öppna konsolen. Om webbläsaren inte har den här metoden eller om du behöver hjälp använder du dokumentationslänkarna nedan för den webbläsare som du använder:

<table>
<tbody>
<tr>
<td><a href="https://www.technipages.com/mac-os-x-enable-web-inspector-in-safari">Safari</a></td>
<td><a href="https://developer.mozilla.org/en-US/docs/Tools/Web_Console/Opening_the_Web_Console">Firefox</a></td>
<td><a href="https://developers.google.com/web/tools/chrome-devtools/?hl=en">Krom</a></td>
<td><a href="https://www.opera.com/dragonfly/documentation/">Opera</a></td>
<td><a href="https://msdn.microsoft.com/en-us/library/gg589512(v=vs.85).aspx#OpeningTools">Internet Explorer</a></td>
</tr>
</tbody>
</table>

I vissa webbläsare kanske inte konsolen visas automatiskt när du öppnar utvecklarverktygen - koden för webbplatsen kan visas först. Om detta händer dig klickar du på alternativet Konsol i utvecklarfönstret och tar skärmbilder av eventuella fel som visas där.

Skicka en biljett till vårt supportteam med **felbilder** och **Commerce Intelligence-kontots e-postadress**.

## Ser du inga fel eller så är du bara vilse?

Oroa dig inte! Skicka in en ny supportanmälan (lägg in e-postadressen till ditt Commerce Intelligence-konto) så får du tillbaka till ditt konto så snart som möjligt.

## Relaterade ämnen i vår kunskapsbas för support:

* [Lägga till en ny användare och ange behörigheter](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/user-management.html)
* [Hur uppdaterar jag min e-postadress eller mitt lösenord?](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/create-user.html)
* [Hur återställer jag mitt lösenord?](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/reset-password.html)
