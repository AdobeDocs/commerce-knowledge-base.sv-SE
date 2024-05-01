---
title: Felsökning av delad åtkomst
description: '**Problem:** Du vill ge delad åtkomst till din betrodda kollega, men du kan inte hitta fliken **Delad åtkomst** på din kontosida för Commerce.'
exl-id: 9e03c031-2359-42a6-9de4-943451a16456
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Felsökning av delad åtkomst

## Jag ser inte [!UICONTROL Shared Access] på min Commerce-kontosida (kontoägare)

**Problem:** Du vill ge din betrodda kollega delad åtkomst, men du kan inte hitta **[!UICONTROL Shared Access]** på din Commerce-kontosida.

**Möjlig orsak:** Behörigheter som krävs för att bevilja delad åtkomst har inte kopplats till ditt Commerce-konto.

**Lösning:** Om du är kontoägare (primär kontoinnehavare) kontaktar du kontoteamet eller [skapa en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). Ange ditt namn och den e-postadress som är kopplad till ditt konto.

>[!NOTE]
>
>Även en icke-kontoägare kan ha **[!UICONTROL Shared Access]** fliken på deras konto. Det är dock bara kontoägaren (primär kontoinnehavare) som har behörighet att ge delad åtkomst till andra användare. Mer information om delad åtkomst finns i [DELAD ÅTKOMST: BEVILJA ÅTKOMST TILL DITT KONTO FÖR ANDRA ANVÄNDARE](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#shared-access) i Adobe Commerce Help Center User Guide.

## Jag har använt delad åtkomst men kan inte få åtkomst till en viss resurs

**Problem:** Jag har växlat till kontot för delad åtkomst men kan inte komma åt **[!UICONTROL Support tab]** (till exempel).

**Möjlig orsak:** Supportberättigandena har upphört att gälla eller så har du inte beviljats delad åtkomst till supporten.

**Lösning:**

1. Växla tillbaka till **[!UICONTROL My Account]**.
1. Klicka sedan på **[!UICONTROL Shared with me]** -fliken.
1. Klicka på **[!UICONTROL Shared Access]** som du har problem med och undersöker vilka resurser du har fått åtkomst till.
1. Om den specifika resursen saknas kan du kontakta kontoägaren (primär kontoinnehavare).

Om du fortfarande har problem kontaktar du kontoteamet på Adobe eller skickar ett e-postmeddelande till grp-Magento-HelpCenterLoginIssues@adobe.com. Ange ditt namn och den e-postadress som är kopplad till ditt konto.

## Jag använde delad åtkomst men ser fortfarande mina biljetter istället för de delade

**Problem:** Jag går till Help Center med delad åtkomst men ser fortfarande bara de biljetter som tillhör mitt eget konto (organisation). På Commerce-kontosidan visas att jag använder kontot för den organisation som har gett mig delad åtkomst, men organisationsbiljetterna visas fortfarande inte.

**Möjlig orsak:** Webbläsaren använder det cachelagrade innehållet från Help Center.

**Lösning:** Rensa webbläsarcachen och öppna hjälpcentret igen (kontrollera att du har växlat till delad åtkomst på din Commerce-kontosida).

## Relaterad läsning

[Formulär för att skicka biljetter: handlaren visas inte i den nedrullningsbara listan Organisation](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed) i vår kunskapsbas för support.
