---
title: Felsökning av delad åtkomst
description: '**Problem:** Du vill ge delad åtkomst till din betrodda kollega, men du kan inte hitta fliken **Delad åtkomst** på din kontosida för Commerce.'
exl-id: 9e03c031-2359-42a6-9de4-943451a16456
feature: Cache
role: Developer
source-git-commit: e77322c04c7245538c10dfb397094eee6cfe6be9
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# Felsökning av delad åtkomst

## Jag kan inte se fliken [!UICONTROL Shared Access] på min Commerce-kontosida (kontoägare)

**Problem:** Du vill ge delad åtkomst till din betrodda kollega, men du kan inte hitta fliken **[!UICONTROL Shared Access]** på Commerce-kontosidan.

**Möjlig orsak:** Behörigheter som krävs för att bevilja delad åtkomst har inte kopplats till ditt Commerce-konto.

**Lösning:** Om du är kontoägare (primär kontoinnehavare) kontaktar du ditt Adobe-kontoteam eller [skapar en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). Ange ditt namn och den e-postadress som är kopplad till ditt konto.

>[!NOTE]
>
>Det är möjligt även för en annan ägare än kontoägaren att ha fliken **[!UICONTROL Shared Access]** på sitt konto. Det är dock bara kontoägaren (primär kontoinnehavare) som har behörighet att ge delad åtkomst till andra användare. Mer information om delad åtkomst finns i [DELAD ÅTKOMST: BEHÖRIGHET FÖR ANDRA ANVÄNDARE ATT FÅ ÅTKOMST TILL DITT KONTO](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#shared-access) i användarhandboken för Adobe Commerce Help Center.

## Jag har använt delad åtkomst men kan inte få åtkomst till en viss resurs

**Problem:** Jag har växlat till kontot för delad åtkomst men kan inte komma åt **[!UICONTROL Support tab]** (till exempel).

**Möjlig orsak:** Supportberättigandena har upphört att gälla eller så har du inte beviljats delad åtkomst till supporten.

**Lösning:**

1. Växla tillbaka till **[!UICONTROL My Account]**.
1. Klicka sedan på fliken **[!UICONTROL Shared with me]**.
1. Klicka på kontot **[!UICONTROL Shared Access]** som du har problem med och kontrollera vilka resurser du har fått åtkomst till.
1. Om den specifika resursen saknas kan du kontakta kontoägaren (primär kontoinnehavare).

Om du fortfarande har problem kontaktar du kontoteamet på Adobe eller skickar ett e-postmeddelande till grp-Magento-HelpCenterLoginIssues@adobe.com. Ange ditt namn och den e-postadress som är kopplad till ditt konto.

## Jag använde delad åtkomst och klickade på [!UICONTROL Support], men när jag öppnade en ny biljett visas inte listrutan [!UICONTROL Organization]

**Problem:** Jag har växlat till kontot för delad åtkomst men kan inte komma åt **[!UICONTROL Support tab]** (till exempel).

**Möjlig orsak:** Du har bara beviljats delad åtkomst till en handlare i ditt konto.

**Lösning:**

1. Växla tillbaka till **[!UICONTROL My Account]**.
1. Om den bara visar en **[!UICONTROL Shared Name]** är det den *standardorganisation* som dina biljetter kommer att öppnas under.

Om du fortfarande har problem kontaktar du ditt Adobe-kontoteam eller skickar ett e-postmeddelande till grp-Magento-HelpCenterLoginIssues@adobe.com. Ange ditt namn och den e-postadress som är kopplad till ditt konto.

## Jag använde delad åtkomst men ser fortfarande mina biljetter istället för de delade

**Problem:** Jag kommer åt Help Center via delad åtkomst men ser fortfarande bara biljetterna som tillhör mitt eget konto (organisation). På Commerce-kontosidan visas att jag använder kontot för den organisation som har gett mig delad åtkomst, men organisationsbiljetterna visas fortfarande inte.

**Möjlig orsak:** Webbläsaren använder det cachelagrade innehållet från Help Center.

**Lösning:** Rensa webbläsarcachen och öppna hjälpcentret igen (kontrollera att du har växlat till delad åtkomst på din Commerce-kontosida).

## Relaterad läsning

[Formulär för anmälan av biljett: handlaren visas inte i listrutan Organisation](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed) i vår kunskapsbas för support.
