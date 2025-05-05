---
title: Experience League Support User Guide for Adobe Commerce
description: Lär dig hur du skickar en supportanmälan till Experience League Support, ger delad åtkomst till konton och navigerar i Adobe Commerce Knowledge Base.
exl-id: 9eb4814f-c9c4-4dd0-b68a-87d712898aa5
feature: Support, Roles/Permissions, Tools and External Services, Admin Workspace, Iaas, Marketing Tools
source-git-commit: 145fc1dfc197cde39d55ceac4d02ecee6c641459
workflow-type: tm+mt
source-wordcount: '2966'
ht-degree: 0%

---

# Experience League Support User Guide for Adobe Commerce

Läs om hur du skickar en supportanmälan till [Experience League Support](https://experienceleague.adobe.com/home?lang=sv-SE#support) och ger delad åtkomst till Adobe Commerce-konton i den här guiden.

>[!NOTE]
>
>Adobe Commerce support har migrerats från Adobe Commerce Help Center till Experience League. Använd det formulärflöde för Experience League som beskrivs [här](#what-is-experience-support) för att skicka supportärenden.

>[!NOTE]
>
>För att kunna se dina tidigare inskickade ärenden på Adobe Commerce Help Center måste du nu gå till https://support.magento.com/hc/en-us/requests eftersom dessa fall inte har migrerats till det nya supportsystemet. Hjälpcentret är nu skrivskyddat. Om du vill fortsätta få stöd för det ursprungliga problemet måste du skicka en uppföljningsanmälan till [Experience League Support](https://experienceleague.adobe.com/home?lang=sv-SE#support).

>[!NOTE]
>
>Kunskapsbasen i Adobe Commerce Help Center har migrerats till Adobe Experience League-portalen. När du skapar en supportanmälan kommer du att få förslag på relaterade artiklar i kunskapsbasen tillsammans med annan relevant Adobe Commerce-dokumentation från Adobe Experience League.

**Viktig uppdatering:** 29 juli 2024

**[VAD STÖDER EXPERIENCE LEAGUE?](#what-is-experience-support)**

**[SUPPORTÄRENDEN](#support-cases)**

* [Logga in på Experience League Support](#sign-in-experience-support)
* [Skicka ett supportärende](#submit-case)

   * [Startsida för Adobe Experience League](#experience-league-start-page)
   * [Adobe Commerce kontosida](#submit-case-adobe-commerce-account-page)
   * [*Verifiera din e-postadress*](#verify-email-address-error)

* [Spåra era supportärenden](#track-support-cases)
* [Kommentarer](#comments-in-your-case)
* [Stäng ärendet](#close-case)
* [Öppna ärendet igen](#reopen-case)
* [Skicka biljett med molnkonsolen](#cloud-console)
* [Adobe Commerce P1 hotline](#P1-hotline)
* [Operativmodellen Adobe Commerce Shared Responsibility](#shared-responsibility-operational-model)

**[DELAD ÅTKOMST: BEHÖRIGHET FÖR ANDRA ANVÄNDARE ATT FÅ ÅTKOMST TILL DITT KONTO](#shared-access)**

* [Vem kan ge delad åtkomst?](#who-can-provide-shared-access)
* [Ge delad åtkomst](#provide-shared-access)
* [Återkalla (ta bort) delad åtkomst](#revoke-shared-access)

   * [Hur tar jag bort användare som beviljats delad åtkomst via ett Cloud-projekt?](#remove-cloud-shared-access-users)

* [Åtkomst till delat konto (växlingskonton)](#switch-accounts)
* [Felsökning av delad åtkomst](#troubleshooting-shared-access)

**[FAKTURERINGSFRÅGOR FÖR ADOBE COMMERCE](#billing-faq)**


## VAD STÖDER EXPERIENCE LEAGUE? {#what-is-experience-support}

Experience League Support är en supportportal för Adobe där Adobe Commerce-kunder kan skicka in och hantera supportärenden. Här kan du även läsa felsökningsartiklar.

## STÖDFALL {#support-cases}

Med Adobe Experience Clouds supportfallshantering kan ni arbeta med support genom olika ärenden för att åtgärda specifika problem som uppstår när Adobe-produkter, inklusive Adobe Commerce, används för alla Adobe Commerce-produkter som omfattas av avtal.

## LOGGA IN PÅ EXPERIENCE LEAGUE SUPPORT {#sign-in-experience-support}

Om du loggar in kan du skicka, uppdatera och besvara frågor från agenter på supportärenden.

Så här loggar du in på Adobe Experience League Support:

1. Navigera till [experience.adobe.com](https://experienceleague.adobe.com/sv).
1. Logga in med dina inloggningsuppgifter för Adobe.

![inloggning-experience-leag](assets/experience_league_sign_in.png)

### Skicka ett supportärende {#support-case}

När du har loggat in som kontoägare eller användare med delad åtkomst kan du skicka ett supportärende via Adobe Experience Leagings hemsida, din Adobe Commerce-kontosida och din kontosida för Adobe Commerce Cloud.

>[!NOTE]
>
>Supportförfrågningar för Adobe Commerce Marketplace-teamet kan inte skickas via Experience League eftersom deras supportsystem fungerar på en separat plattform som inte är integrerad med Experience League.
>
>Du kan skicka in ditt supportärende om följande uppgifter är sanna:
>
>* Organisationen i fråga har ett namn i den vänstra kolumnen och slutar i ([!DNL Commerce]). Problemet är relaterat till den organisationen eller ett konto som är kopplat till den.
>* Problemet är att du inte kan logga in på Marketplace-kontot eller att du har en fråga om att distribuera ett tillägg.
>* Ditt problem handlar inte bara om att begära återbetalning för ditt Marketplace-inköp.
>
>Om du har problem med att publicera tillägget, har problem med att köpa eller begär en återbetalning på [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/) måste du kontakta [!DNL Commerce Marketplace]-teamet direkt på https://commercemarketplace.adobe.com/. Navigera till nederkanten av sidan och klicka på **[!UICONTROL Contact Us]**, som öppnar ett formulär för att skicka ett supportärende på Marketplace.

#### Startsida för Adobe Experience League {#experience-league-start-page}

Följ de här stegen för att skicka in ett nytt supportärende från Adobe Experience Leagas startsida:

>[!INFO]
>
>1. För att kunna lämna in ett ärende måste du ha rätt till support för lämplig produkt (t.ex. Adobe Commerce, Adobe Commerce Intelligence, Adobe Commerce Payment Services, Experience Platform). Om du inte har rätt till support visas ett fält högst upp på sidan som informerar dig om att du inte är en supportberättigad användare i organisationen.
>1. Om du tillhör flera organisationer eller om det finns flera organisationer med liknande namn (var och en representerar någon av de andra Adobe-produkter som organisationen prenumererar på) måste du först välja rätt organisation i listrutan i den vänstra kolumnen som slutar i *[!DNL (Commerce)]*.
>1. Om du inte ser Adobe Commerce i listrutan [!UICONTROL Select a product] när du skickar ett Commerce-relaterat ärende måste du först få [delad åtkomst](#shared-access) från Commerce-kontoägare.

>[!NOTE]
>
>Se till att du har valt rätt organisation innan du skickar in ärendet och att den organisation du har valt har rätt behörighet för den produkt som du begär support för. Om ditt problem till exempel är relaterat till Adobe Commerce, men du har valt Adobe Commerce Intelligence eller Adobe Experience Platform som produkt och ärendet har skickats in, kan detta leda till felhantering av ditt ärende och förseningar i svarstiderna.
>
>Om fel organisation valdes när ärendet skickades kan ditt team inte visa ärendet under [!UICONTROL My Cases] för rätt/korrekt organisation. Adobe Commerce supportteam har inte möjlighet att ändra den organisation som är kopplad till ärendet. För att kunna åtgärda detta måste du stänga det befintliga ärendet och skicka in ett nytt ärende med den information som anges/valts.

1. Klicka på **Support** i sidhuvudet. På sidan Support öppnas.

   ![open-support-page](assets/click_support.png)

1. Kontrollera att du har valt lämplig organisation i listrutan Organisation (om den är synlig) för att starta processen för supportintag. Om du vill skicka ett ärende för Adobe Commerce väljer du organisationens namn som slutar på *[!DNL Commerce]*.

   ![select_appropriate_org](assets/select_appropriate_org.png)

1. Klicka på **[!UICONTROL Open Ticket]** på den vänstra menyn eller klicka på **[!UICONTROL Get Started]** i *[!UICONTROL Open a support ticket]*-kortet.

   ![open-support-case](assets/open_support_case.png)

1. Välj en produkt i listrutan och ange en falltitel och beskrivning. Obs! Om listrutan inte visar några produkter eller om [!DNL Commerce] inte är ett tillgängligt alternativ kan du försöka med att växla [!UICONTROL Organization] i den vänstra kolumnen och sedan kontrollera igen.

   ![select_product](assets/support_case_product.png)

   >[!NOTE]
   >
   >Om du skickar in en biljett med **[!DNL Commerce]i molninfrastrukturen** som har valts som produkt och organisationen har flera projekt listade, uppmanas du att välja rätt [!UICONTROL Project ID]. Om du inte kan hitta det önskade [!UICONTROL Project ID] måste du lägga till en anteckning på biljetten om att du söker hjälp med ett annat X-projekt.<br>Om du tänker skicka in en **[!DNL Commerce]på Managed Services**-biljett och är på **[!DNL Commerce]i molninfrastrukturen**, men inte **[!DNL Commerce]i molninfrastrukturen** som en tillgänglig produkt:<br>1. Ange ett ämne för din utgåva i **[!UICONTROL Case title]**.<br>2. Ange en beskrivning av ditt problem i **[!UICONTROL Case description]**.<br>3. När du har angett båda dessa objekt visas fältet **[!UICONTROL Cloud Project URL]** nedan.


1. Adobe Experience League kommer att föreslå artiklar och bästa praxis som kan hjälpa er att lösa ert ärende. Om du fortfarande behöver direktsupport måste du ange ytterligare information innan du skickar in ärendet.

   ![direct_support_required](assets/direct_support.png)

1. När du har fyllt i all nödvändig information klickar du på **[!UICONTROL Submit case]**.

>[!IMPORTANT]
>
>Om du inte kan se din organisation i listrutan för organisationen när du loggar in på experienceleague.adobe.com, kan du behöva synkronisera din profil med accounts.magento.com innan du begär support eller hanterar ett befintligt supportärende.
>
>1. Navigera till accounts.magento.com och logga in med samma profil (företag, skola eller personlig) som du använder för att hantera supportärenden i Adobe Experience League.
>1. När du har loggat in på din accounts.magento.com går du tillbaka till experienceleague.adobe.com och loggar in.
>1. Välj din organisation i listrutan för organisation.
>1. Om din organisation fortfarande inte visas kontaktar du Commerce-administratören för att få behörighet som supportrepresentant. Mer information finns i hjälpartikeln för [Commerce Account Share](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/commerce-account/commerce-account-share).

>[!NOTE]
>
>Varför organisationen/produkten är viktig
>
>**Exempel A**: Du har bara delad åtkomst till ett företag och det företaget har berättiganden för två Adobe-produkter: Produkt1 och Produkt2.
>
>1. Eftersom varje organisation representerar en produkt visas två organisationer i listrutan, t.ex. OrgA-Product1 och OrgB-Product2.
>1. Om du valde Produkt = Produkt1 men problemet är relaterat till Produkt2, dirigeras ärendet till support för Produkt2 och det kommer att bli fördröjt när ärendet överförs till support för Produkt1.
>1. Om du har skickat in ärendet för OrgA-Product1 och vill granska [!UICONTROL My Cases] för den organisationen i framtiden, kommer du inte att se det om du väljer OrgA-Product2 som organisation (du skulle bara behöva välja den andra organisationen, jämfört med exempel B).
>
>**Exempel B**: Du har delad åtkomst till två företag, och varje företag har bara berättiganden för Adobe Commerce.
>
>1. Om du har skickat in ärendet för OrgA men problemet faktiskt påverkar OrgB, kommer medlemmar i OrgB inte att kunna se det här fallet under [!UICONTROL My Cases] i framtiden.
>1. Dessutom kan medlemmar i OrgA se fall under [!UICONTROL My Cases] som faktiskt är avsedda för OrgB, vilket kan leda till sekretessproblem.

Du måste ha ett konto på både https://account.adobe.com och https://account.magento.com för att kunna logga in på Experience League och skicka in ett supportärende. Du kan inte skicka in ett supportärende förrän du är inloggad.

>[!NOTE]
>
>Om du redan har ett konto på https://account.magento.com, men inte kan logga in, kanske du inte har registrerat dig för ett konto på https://account.adobe.com, vilket krävs från och med augusti 2022.
>
>Så här löser du det:
>
>1. Skapa ett konto på https://account.adobe.com med samma e-postadress på ditt MAG-ID.
>1. Gå till https://account.magento.com om du vill länka din Adobe ID till ditt MAG-ID.

#### Adobe Commerce kontosida {#submit-case-adobe-commerce-account-page}

Så här skickar du en ny supportanmälan på din Adobe Commerce-kontosida:

1. Logga in på ditt Adobe Commerce-konto. Se [detaljerade instruktioner](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-create.html?lang=sv-SE#create-a-commerce-account) i vår användarhandbok.
1. Klicka på fliken **Support**.

   ![magento_account_support_tab](assets/magento_account_support_tab.png){width="800"}

1. Adobe Experience Leagas supportsida laddas för er.
1. Välj **[!UICONTROL Open Ticket]** på den vänstra menyn.
1. Fyll i [fälten](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/faq/support-ticket-contact-reason-descriptions).
1. Klicka på **Skicka**.

#### *Verifiera din e-postadress*-fel på Adobe Commerce-kontosida {#verify-email-address-error}

Du kan inte skicka in en supportanmälan om du får felmeddelandet Kontrollera din e-postadress som liknar den nedan på sidan [Adobe Commerce-konto](https://account.magento.com/).

![Verify_Email_Address_Error](assets/Verify_Email_Address_Error.png)


### Spåra era supportärenden {#track-support-case}

Dina supporttillfällen är sådana som du har:

* har lämnat in personuppgifter.
* har lagts till som en bevakare via en CC (kopia).

#### Visa dina ärenden

Du kan visa de ärenden som du har skickat personligen genom att klicka på **[!UICONTROL My Cases]** på den vänstra menyn. Se till att du har valt rätt organisation som slutar med &quot;(Commerce)&quot;.

![view-support-cases](assets/view_support_cases.png)

#### Visa historikärenden från Adobe Commerce Help Center

Läs mer om hur du kan **visa dina historiska fall** från Adobe Commerce Help Center i [Avställning av Adobe Commerce Help Center](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/news/decommissioning-of-adobe-commerce-help-center) i Adobe Commerce Knowledge Base.

#### Visa bevakade ärenden

Du kan visa de ärenden som du har *lagts till som en bevakare* genom att klicka på **[!UICONTROL My organization's cases]** på den vänstra menyn.

<!-- TODO: Add image here -->


#### Sök efter ärenden

Om du vill söka efter fall skriver du din sökfråga i fältet *[!UICONTROL Search]* och trycker på *enter* på tangentbordet.

![sökfall](assets/search_cases.png)

#### Eskalera dina ärenden

Om du känner att ett fall kräver ytterligare uppmärksamhet och att vår initiala svarstid har passerat, kan du eskalera fallet. För att göra det,

1. Klicka på **[!UICONTROL Escalate to management]** längst ned till höger på panelen *[!UICONTROL Case Detail]* till höger på skärmen.

   ![eskalera till hantering](assets/escalate_to_management.png)

1. När du har klickat visas ett popup-formulär. Fyll i formuläret och klicka sedan på **[!UICONTROL Escalate]**.

   ![bekräfta-eskalering](assets/confirm_escalation.png)

   *Orsaker till eskalering kan vara*: Agentkommunikationskunskaper, Agentens tekniska kunskap, Väntar på återanrop/uppdatering, Ändring i problemnödläge, Upplösningen uppfyllde inte förväntningarna eller Tid till lösning.

#### Lägg till en bevakare i supportärenden

Du kan lägga till bevakare för supportärenden som skickats in av medlemmar i din organisation. Tittarna får e-postmeddelanden när nya ärenden skickas eller när befintliga ärenden uppdateras.

1. Om du vill lägga till en bevakare i ett befintligt ärende öppnar du skiftläget och klickar på pennikonen bredvid &quot;bevakare&quot; på panelen Skiftinformation till höger på skärmen.

   ![add-watchers](assets/add_watchers.png)

1. När du har klickat på pennan kan du lägga till eller ta bort bevakare från listan.

   ![update-watchers](assets/update_watchers.png)

### Kommentarer {#comments-in-your-case}

Kommentarerna i ditt ärende innehåller alla kommentarer som skrivits av dig eller Adobe Commerce supportteam. Kommentarerna visas från den senaste (överst) till den tidigaste (nederst).
Så här lägger du till en kommentar:

1. Rulla längst ned på biljetten.
1. Skriv din kommentar i fältet **[!UICONTROL Comments]** och klicka på **[!UICONTROL Add comments]**.

![add-comments](assets/add_comments.png)

### Stäng ärendet {#close-case}

Om du vill stänga ditt ärende klickar du på **[!UICONTROL Close case]** längst ned till höger på panelen *[!UICONTROL Case Detail]*.

![close-case](assets/close_case.png)

### Öppna ärendet igen {#reopen-case}

Om du vill öppna ditt ärende igen svarar du på e-postmeddelandet från vårt supportsystem som gäller det ärendet och ber agenten att öppna det igen. Om du gör detta inom 14 dagar efter att ärendet stängts kan handläggaren ta ärendet vidare. Men om det är efter 14 dagar måste handläggaren skapa ett nytt ärende.

### Skicka biljett med molnkonsolen {#cloud-console}

Så här skickar du en ny supportanmälan via molnkonsolen:

1. Logga in på [molnkonsolen](https://console.adobecommerce.com).
1. Välj **[!UICONTROL Support]** på användarmenyn.
1. Sidan **[!UICONTROL My Tickets]** visas.
1. Klicka på **[!UICONTROL Submit a ticket]** i det övre högra hörnet.
1. Fyll i [fälten](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/faq/support-ticket-contact-reason-descriptions).
1. Klicka på **[!UICONTROL Submit]**.

### Adobe Commerce P1 hotline {#P1-hotline}

[Adobe Commerce P1 hotline](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html?lang=sv-SE) -artikeln innehåller P1-hotline-nummer för Adobe Commerce när man söker hjälp under en P1-incident och förklarar vilken information som ska anges.

### Operativmodellen Adobe Commerce Shared Responsibility {#shared-responsibility-operational-model}

Läs artikeln om [Adobe Commerce Shared Responsibility Operational Model](https://experienceleague.adobe.com/sv/docs/commerce-operations/security-and-compliance/shared-responsibility#operational-responsibilities-summary),
som syftar till att förtydliga det operativa ansvaret för vår Pro-infrastruktur.

### Öppna en uppföljningsbiljett {#follow-up}

Genom att öppna en uppföljningsbiljett säkerställs att den ursprungliga utgåvan är länkad till uppföljningsbiljetten för kontinuitet.

Om du vill öppna en uppföljningsbiljett klickar du på länken *Skapa en uppföljning* längst ned på biljetten som du vill skapa en uppföljning till.

## DELAD ÅTKOMST: BEVILJA ÅTKOMST TILL DITT KONTO FÖR ANDRA ANVÄNDARE {#shared-access}

Du kan ge andra Adobe Commerce-kontoinnehavare begränsad åtkomst till ditt konto. Om du använder funktionen **delad åtkomst** kan du ge betrodda anställda och tjänsteleverantörer behörighet att använda ditt Help Center-konto så att de kan arbeta med dina supportärenden.

Du kan tillhandahålla och hantera delad åtkomst via din Adobe Commerce-kontosida på [https://account.magento.com](https://account.magento.com/).

### Vem kan ge delad åtkomst? {#who-can-provide-shared-access}

Det är bara kontoägaren (primär kontoinnehavare) som kan ge andra användare delad åtkomst.

Det är kundens ansvar att hantera användare och deras åtkomst, särskilt när det gäller delad åtkomst. Adobe Commerce supportteam kan alltså inte ge delad åtkomst till ett Adobe Commerce-konto åt en kund. Kunder uppmuntras att lägga till användare med delad åtkomst själva med hjälp av [Adobe Commerce-kontosidan](https://account.magento.com/).

Användare som har fått delad åtkomst kan inte överföra eller ge sådan åtkomst till andra användare.

### Ge delad åtkomst {#provide-shared-access}

I avsnittet [Dela ett Commerce-konto](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/commerce-account/commerce-account-share) i Adobe Commerce Starthandbok finns mer information om hur du konfigurerar ett delat konto.

>[!NOTE]
>
>Användaren måste ha ett befintligt konto innan han/hon kan beviljas delad åtkomst - se [Skapa ett Commerce-konto](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/commerce-account/commerce-account-create#create-a-commerce-account) för mer information.

När en ny användare har fått delad åtkomst är den relaterade informationen tillgänglig i **Delad åtkomst** > **Hantera behörigheter** på din Adobe Commerce-kontosida.

>[!NOTE]
>
>Delad åtkomst ger inte automatiskt åtkomst till Commerce Cloud Console. Du måste [lägga till användaren separat i molnprojektet](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/project/user-access#add-a-user-to-the-project).

![magento-account-shared-manage-permissions](assets/magento_account_shared_manage_permissions.png)

### Återkalla (ta bort) delad åtkomst {#revoke-shared-access}

1. Logga in på ditt Adobe Commerce-konto på [https://account.magento.com](https://account.magento.com/).
1. Välj **Hantera behörigheter i panelen till vänster under Delad åtkomst.**
1. Hitta användaren som du vill återkalla delad åtkomst från och klicka på ![Ta bort ikon](assets/remove_icon.png){width="25"} i användarens rad (**Åtgärder** kolumn).
1. Klicka på **Ta bort användare** om du vill återkalla åtkomst eller på X i det övre hörnet om du vill avbryta återkallandet.

   ![revoke_shared_access](assets/revoke_shared_access.png){width="800"}

   Du kan också återkalla delad åtkomst via menyn **Redigera**:

1. Logga in på ditt Adobe Commerce-konto på [https://account.magento.com](https://account.magento.com/).
1. Välj **Hantera behörigheter i panelen till vänster under Delad åtkomst.**
1. Hitta användaren som du vill återkalla delad åtkomst från och klicka på **Redigera** i användarens rad (**Åtgärder** kolumn).
1. Klicka på **Ta bort den här användaren** längst ned på sidan.
1. Klicka på **Ta bort användare** i bekräftelserutan om du vill återkalla åtkomst eller på X i det övre hörnet om du vill avbryta återkallningen.

### Hur tar jag bort användare som beviljats delad åtkomst via ett Cloud-projekt? {#remove-cloud-shared-access-users}

<u>Berörda produkter och versioner</u>

* Adobe Commerce Cloud (alla versioner)

<u>Orsak</u>

Om du har/har haft ett Adobe Commerce Cloud-projekt och har lagt till en användare i projektet, kan de automatiskt ha fått delad åtkomst på Projektägarens MAGE-ID. Detta anges normalt i kolumnen **[!UICONTROL Share Name]** och visar *Cloud Shared Access från MAG[XYZ]*.

>[!NOTE]
>
>Om länken DELETE saknas innebär det att delad åtkomst automatiskt beviljades via Commerce Cloud.

<u>Lösning</u>

Det går inte att ta bort listan över användare med delad åtkomst med resursnamnet *Cloud-delad åtkomst från MAG[XYZ]* om den delade åtkomsten inte lades till/gavs [på den här sidan](https://account.magento.com/grantor/manage/). Dessa bevaras i informations-/revisionssyfte.

När du har återkallat behörigheten för dessa användare med delad åtkomst har de inte längre den åtkomsten.

1. Logga in på ditt Adobe Commerce-konto på [https://account.magento.com](https://account.magento.com/).
1. Välj **[!UICONTROL Manage Permissions]** under *[!UICONTROL Shared Access]* på panelen till vänster.
1. Hitta användaren som du vill återkalla delad åtkomst från och klicka på **[!UICONTROL Edit]** i användarens rad (*[!UICONTROL Actions]* kolumn).
1. Avmarkera alla resurser under *[!UICONTROL Grant Account Permissions]*.

![grant-account-permissions-image](assets/help-center-user-guide-grant-account-permissions-image.png){width="800"}

Mer information finns i dokumentationen [Hantera användaråtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=sv-SE#manage-users-from-the-project-web-interface) i vår Commerce om molninfrastrukturguide.

### Åtkomst till delat konto (växlingskonton) {#switch-accounts}

Följ de här stegen för att använda den delade åtkomst du fått:

1. Logga in på ditt Adobe Commerce-konto på [https://account.magento.com](https://account.magento.com/).
1. Klicka på menyn **Byt konto** och välj ett konto.

   ![magento-account-shared-switch](assets/magento_account_shared_switch.png){width="800"}

Om du vill veta vilket konto du använder (ditt eget ursprungliga konto eller delad åtkomst) kan du gå till menyn **Byt konto**: där visas det aktiva kontot.

### Felsökning av delad åtkomst {#troubleshooting-shared-access}

Se artikeln [Felsökning av delad åtkomst](/help/troubleshooting/miscellaneous/shared-access-troubleshooting.md) i vår kunskapsbas för support.

## FAKTURERINGSFRÅGOR FÖR ADOBE COMMERCE {#billing-faq}

Handlare betalar vanligtvis för våra tjänster med en kreditkortstransaktion (CC), och denna [Vanliga frågor om fakturering för Adobe Commerce](/help/faq/general/billing-faq-for-adobe-commerce.md) är en resurs som du kan använda när du betalar din faktura.


