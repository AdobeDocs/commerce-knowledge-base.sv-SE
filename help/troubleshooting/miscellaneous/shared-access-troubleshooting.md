---
title: Felsökning av delad åtkomst
description: '**Problem:** Du vill ge delad åtkomst till din betrodda kollega, men du kan inte hitta fliken **Delad åtkomst** på din kontosida för Commerce.'
exl-id: 9e03c031-2359-42a6-9de4-943451a16456
feature: Cache
role: Developer
source-git-commit: 6529a7d2c080a410617af8c51893c79c65c0bb81
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# Felsökning av delad åtkomst

## Jag kan inte se fliken [!UICONTROL Shared Access] på min Commerce-kontosida (kontoägare)

**Problem:** Du vill ge delad åtkomst till din betrodda kollega, men du kan inte hitta fliken **[!UICONTROL Shared Access]** på Commerce-kontosidan.

**Möjlig orsak:** Behörigheter som krävs för att bevilja delad åtkomst har inte associerats med ditt Commerce-konto.

**Lösning:**

* Om du är kontoägare (primär kontoinnehavare) kontaktar du ditt Adobe-kontoteam. Om din teammedlem har tillgång till support ber du dem [skapa en supportanmälan](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#merchant-not-displayed). Ange namn och e-postadress som är kopplad till ditt konto.
* Om du inte är kontoägare måste du kontakta dem för att ge delad åtkomst och nödvändiga behörigheter.
* Om kontoägaren inte längre är hos företaget och du vill överföra kontot till en annan användare, se [Överför ett Commerce-konto](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-transfer).

>[!NOTE]
>
>Det är möjligt även för en annan ägare än kontoägaren att ha fliken [!UICONTROL Shared Access] på sitt konto. Det är dock bara kontoägaren (primär kontoinnehavare) med de nödvändiga behörigheterna som kan ge delad åtkomst till andra användare. Mer information om delad åtkomst finns i [Delad åtkomst: Bevilja andra användare behörighet att komma åt ditt konto](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#shared-access) i användarhandboken för Experience League Support för Adobe Commerce.

## Jag har använt delad åtkomst men kan inte få åtkomst till en viss resurs

**Problem:** Jag har växlat till [!UICONTROL Shared Access]-kontot men kan inte komma åt **[!UICONTROL Support tab]** (till exempel).

**Möjlig orsak:** Stödrättigheterna har upphört att gälla eller så har du inte beviljats delad åtkomst till support.

**Lösning:**

1. Växla tillbaka till **[!UICONTROL My Account]**.
1. Klicka på fliken **[!UICONTROL Shared with me]**.
1. Klicka på kontot **[!UICONTROL Shared Access]** som du har problem med och kontrollera vilka resurser du har fått åtkomst till.
1. Om den specifika resursen saknas kan du kontakta kontoägaren (den primära kontoinnehavaren).

Kontakta ditt Adobe-kontoteam om du fortfarande har problem. Ange namn och e-postadress som är kopplad till ditt konto.

## Jag använde delad åtkomst och klickade på [!UICONTROL Support], men när jag öppnade en ny biljett för organisationen fanns det ingen tillgänglig produkt i formuläret

**Problem:** Jag kan inte välja lämpligt molnprojekt när jag öppnar en biljett på [Experience League](https://experienceleague.adobe.com/home#support).

**Möjlig orsak:** Du har inte valt rätt organisation med [!DNL Commerce] berättiganden.

**Lösning:**

1. Se till att välja organisationen med suffixet *[!DNL Commerce]*. Det här är den organisation som har [!DNL Commerce] berättiganden.

Kontakta ditt Adobe-kontoteam om du fortfarande har problem. Ange namn och e-postadress som är kopplad till ditt konto.

## Jag använde delad åtkomst och klickade på [!UICONTROL Support], men när jag öppnade en ny biljett för den organisation som har [!DNL Commerce]-berättigandena listades inte molnprojektet i formuläret

**Problem**: Jag kan inte välja rätt molnprojekt när jag öppnar en biljett på [Experience League](https://experienceleague.adobe.com/home#support).

**Möjlig orsak**: Du kanske inte har lagts till i projektet, eller så är projektet kopplat till en annan licens (vissa organisationer kan ha dotterföretag/närstående företag med mycket liknande namn).

**Lösning**:

1. Kontrollera att du har lagts till i projektet. Se [Hantera användaråtkomst](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/user-access).
1. Kontrollera att kontoägaren har gett dig delad åtkomst till licensen som är kopplad till projektet.

Kontakta ditt Adobe-kontoteam om du fortfarande har problem. Ange namn och e-postadress som är kopplad till ditt konto.

## Jag använde delad åtkomst och klickade på [!UICONTROL Support], men när jag öppnade en ny biljett visades inte listrutan [!UICONTROL Organization] eller så listades inte organisationen

**Problem**: Jag växlade till [!UICONTROL Shared Access]-kontot, men när jag försöker skicka en biljett på [Experience League](https://experienceleague.adobe.com/home#support) finns ingen organisation tillgänglig eller så visas inte organisationsnamnet i listrutan.

**Möjlig orsak**: Du har bara beviljats delad åtkomst till en handlare i ditt konto.

**Lösning**:

1. Växla tillbaka till **[!UICONTROL My Account]**.
1. Om det bara finns ett delat namn är det standardorganisationen som dina biljetter öppnas under.

Kontakta ditt Adobe-kontoteam om du fortfarande har problem. Ange namn och e-postadress som är kopplad till ditt konto.

## Jag använde delad åtkomst men ser fortfarande mina biljetter istället för de delade

**Problem:** Jag använder [Help Center](https://support.magento.com/hc/us-en/requests) med delad åtkomst, men ser ändå bara biljetter som tillhör mitt eget konto (organisation). På kontosidan för [!DNL Commerce] visas att jag använder organisationens konto, som har gett mig delad åtkomst, men organisationsbiljetterna visas fortfarande inte.

**Möjlig orsak:** Webbläsaren använder det cachelagrade innehållet från Help Center.

**Lösning:** Rensa webbläsarcachen och öppna hjälpcentret igen (kontrollera att du har växlat till delad åtkomst på din Commerce-kontosida).
