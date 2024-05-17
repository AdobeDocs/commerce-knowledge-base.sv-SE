---
title: Användarhandbok för Adobe Commerce Help Center
description: Lär dig hur du skickar en supportanmälan till Adobe Commerce Help Center, ger delad åtkomst till konton och navigerar i Adobe Commerce Knowledge Base.
exl-id: 9eb4814f-c9c4-4dd0-b68a-87d712898aa5
feature: Support, Roles/Permissions, Tools and External Services, Admin Workspace, Iaas, Marketing Tools
source-git-commit: 86810427e8f902dc184b377257c8e86dd28f38f6
workflow-type: tm+mt
source-wordcount: '3992'
ht-degree: 0%

---

# Användarhandbok för Adobe Commerce Help Center

Läs om hur du skickar en supportanmälan till [Adobe Commerce Help Center](https://support.magento.com/hc/en-us) och ge delad åtkomst till Magento-konton.

>[!NOTE]
>
>Kunskapsbasen i Adobe Commerce Help Center har migrerats till Adobe Experience League-portalen. När du skapar en supportanmälan kommer du att få förslag på relaterade artiklar i kunskapsbasen tillsammans med annan relevant Adobe Commerce-dokumentation från Adobe Experience League.

**Huvuduppdatering:** 14 oktober 2022

**[VAD ÄR ADOBE COMMERCE HELP CENTER?](#what-is)**

**[STÖDTICKAR](#support-tickets)**

* [Logga in på Help Center](#login)
* [Skicka en supportanmälan](#submit-ticket)

   * [Startsida för Help Center](#submit-ticket-help-center-start-page)
   * [Magento-kontosida](#submit-ticket-magento-account-page)
   * [Cloud Console](#submit-ticket-magento-cloud-account-page)
   * [Information i din supportanmälan](#info-in-support-ticket)
   * [Länken Skicka en biljett visas inte på startsidan för Adobe Commerce Help Center](#no-submit-link)
   * [*&quot;Verifiera din e-postadress&quot;*](#verify-email-address)
   * [Formulär för att skicka biljetter: handlaren visas inte i den nedrullningsbara listan Organisation](#merchant-not-displayed)

* [Spåra era biljetter](#track-tickets)
* [Adobe Commerce P1 hotline (inloggning krävs)](#P1-hotline)
* [Operativmodellen Adobe Commerce Shared Responsibility (inloggning krävs)](#shared-responsibility-operational-model)
* [Förklaring av supportbiljettfält](#ticket-fields-explained)
* [Biljettstatus: Hur dina förfrågningar behandlas](#ticket-status)
* [Samtal i din biljett](#conversation-in-ticket)
* [Lös din biljett](#resolve-ticket)
* [Öppna en uppföljningsbiljett](#follow-up)

**[DELAD ÅTKOMST: BEVILJA ÅTKOMST TILL DITT KONTO FÖR ANDRA ANVÄNDARE](#shared-access)**

* [Vem kan ge delad åtkomst?](#who-can-provide-shared-access)
* [Ge delad åtkomst](#provide-shared-access)
* [Återkalla (ta bort) delad åtkomst](#revoke-shared-access)

   * [Hur tar jag bort användare som beviljats delad åtkomst via ett Cloud-projekt?](#remove-cloud-shared-access-users)

* [Åtkomst till delat konto (växlingskonton)](#switch-accounts)
* [Felsökning av delad åtkomst](#troubleshooting-shared-access)

**[FAKTURERINGSFRÅGOR FÖR ADOBE COMMERCE](#billing-faq)**

**[MAGENTO U ÄR NU EN DEL AV ADOBE DIGITALA LÄRNINGSTJÄNSTER](#magento-u)**

## VAD ÄR ADOBE COMMERCE HELP CENTER? {#what-is}

The [Adobe Commerce Help Center](https://support.magento.com/hc/en-us) är en supportportal för Adobe Commerce, där man kan skicka in och hantera supportärenden. Här kan du även läsa felsökningsartiklar.

## STÖDTICKAR {#support-tickets}

Med Adobe Commerce Ticketing System kan du arbeta med supportärenden för att åtgärda just de problem du upplever när du arbetar med Adobe Commerce - för alla Adobe Commerce-produkter.

## LOGGA IN PÅ HJÄLP CENTER {#login}

Med inloggning kan du skicka, uppdatera och besvara frågor från agenter på supportärenden.

Så här loggar du in på Adobe Commerce Help Center:

1. Gå till hjälpcentret på <https://support.magento.com>.
1. Klicka **Logga in** längst upp till höger.

Logga in med autentiseringsuppgifterna för ditt Magento-konto. Mer information finns i [Ditt Magento-konto](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-create.html) i vår användarhandbok.

### <strong>Skicka en supportanmälan</strong> {#submit-ticket}

När du har loggat in kan du skicka in en supportanmälan via hjälpcentrets startsida, din kontosida för Magento och din kontosida för Magento Cloud.

* Om du är **Kontoägare** Följ stegen nedan.
* Om du är **Delad åtkomst-användare, du måste växla konton först** [Åtkomst till delat konto (växlingskonton)](#switch-accounts)och sedan kan du gå vidare till stegen nedan.

#### Startsida för Help Center {#submit-ticket-help-center-start-page}

Så här skickar du en ny supportanmälan på startsidan i Adobe Commerce Help Center:

1. Gå till [Adobe Commerce Help Center](https://support.magento.com/hc/en-us).
1. Klicka **Skicka en biljett** längst upp till höger.

   ![skicka-en-biljett](assets/submit-a-ticket-4.png){width="800"}

1. Fyll i fälten.
1. Klicka **Skicka**.

Du **måste logga in** till hjälpcentret med ditt Magento-konto för att skicka in en supportanmälan. Tills du är inloggad [den **Skicka en biljett** knappen visas inte](#no-submit-link).

#### Magento-kontosida {#submit-ticket-magento-account-page}

Så här skickar du en ny supportanmälan på din kontosida i Magento:

1. Logga in på ditt Magento-konto. Se [detaljerade anvisningar](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-create.html?lang=en#create-a-commerce-account) i vår användarhandbok.
1. Klicka på **Support** -fliken.

   ![magento_account_support_tab](assets/magento_account_support_tab.png){width="800"}

1. Startsidan för Help Center visas.
1. Klicka **Skicka en biljett** längst upp till höger.
1. Fyll i fälten.
1. Klicka **Skicka**.

#### Cloud Console {#submit-ticket-magento-cloud-account-page}

Så här skickar du en ny supportanmälan via molnkonsolen:

1. Logga in på [Cloud Console](https://console.adobecommerce.com).
1. Välj **[!UICONTROL Support]** i användarmenyn.
1. The **[!UICONTROL My Tickets]** sidan läses in.
1. Klicka **[!UICONTROL Submit a ticket]** längst upp till höger.
1. Fyll i fälten.
1. Klicka **Skicka**.
1. Klicka på **[!UICONTROL Submit]**.

#### Information i din supportanmälan {#info-in-support-ticket}

Fälten, markerade med en röd asterisk ( **\*** ), är obligatoriska och måste fyllas i. Om du lämnar något av dessa fält tomt kan du inte skicka in din biljett.

Se [Biljettfält](#ticket-fields-explained) nedan för mer detaljerad information.

### Länken Skicka en biljett visas inte på startsidan för Adobe Commerce Help Center {#no-submit-link}

#### Problem

Du kommer åt Adobe Commerce Help Center och vill skicka in en supportförfrågan, men **Skicka en biljett** -länken visas inte på hjälpcentrets startsida.

#### Orsak

Orsaken kan vara något av följande:

* Du har inte loggat in på Help Center.
* Om du använder delad åtkomst för första gången har du inte utfört de steg som krävs för att säkerställa att Adobe Commerce Help Center har konfigurerats korrekt via SSO-anropet från Magento.com.
* Ditt konto har inte rätt till Adobe Commerce support (du är till exempel inte betalande Commerce-kund eller kund med öppen källkod).

#### Lösning

[Logga in på Help Center](/help/help-center-guide/help-center/magento-help-center-user-guide.md#provide-shared-access).

The **Skicka en biljett** -länken visas endast för kunder med ett e-postmeddelande som är länkat till ett giltigt supportavtal.

#### Använda konto för delad åtkomst

Om du vill kunna använda kontot för delad åtkomst för att skicka supportärenden måste du göra följande (detta behöver bara göras en gång):

1. Efter mottagande [delad åtkomst](https://support.magento.com/hc/en-us/articles/360052444712#who-can-provide-shared-access)loggar du in på [Magento-konto på magento.com webbplats](https://account.magento.com/).
1. I **Byt konto** i det övre högra hörnet väljer du kontot för delad åtkomst.
1. Klicka på **Support** i den vänstra panelen. På så sätt ser du till att Adobe Commerce Help Center är korrekt konfigurerad via SSO-anropet från Magento.com till Adobe Commerce Help Center.

#### Ser du fortfarande inte **Skicka en biljett** link

Om du inte har **Delade konton** under **Byt konto** nedrullningsbar lista, men du arbetar för en kund som har en Adobe Commerce-licens, ber dem att ge dig delad åtkomst. Mer info finns här [Ge delad åtkomst till Magento-kontot](/help/help-center-guide/help-center/magento-help-center-user-guide.md#provide-shared-access).

Om du äger en Adobe Commerce-licens kontrollerar du att du inte har någon faktura med **Väntande betalning** status. Supportberättiganden beviljas automatiskt eller återkallas enligt fakturabetalningsstatus.

<span class="wysiwyg-underline">Kontrollera betalningsstatus</span>:

1. Logga in på [magento.com](https://support.magento.com/).
1. Klicka på **Fakturahistorik** till vänster.
1. Om du **do** har en faktura med **Väntande betalning** status, **kontakta kontoteamet på Adobe** för att få betalningsproblemet löst.

Vi ger support endast till Adobe Commerce licensägare och konton som har delad åtkomst till ett konto med en Adobe Commerce-licens. Om du behöver support för Magento Open Source kan du använda dessa självhjälpsresurser:

* [Adobe Commerce Help Center](https://support.magento.com/)
* [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs/)
* [Dokumentationsresurser för Adobe Commerce](https://experienceleague.adobe.com/docs/commerce.html)
* [Magento forum](https://community.magento.com/?_ga=2.99592990.1084044056.1559046120-720752292.1551793747)

Om du har problem med att logga in på ditt konto eller tror att Delad åtkomst har konfigurerats korrekt kan du fortfarande inte se **Skicka en biljett** knapp, skicka e-post [Hjälpcentrets inloggningsproblem](mailto:grp-magento-helpcenterloginissues@adobe.com)och vi granskar gärna dina kontoinställningar och dina supportberättiganden.

>[!NOTE]
>
>Skicka inte e-post om du kan skicka en biljett, utan i stället har problem med att få åtkomst till ditt molnprojekt. Vänligen skicka in biljetten för det här problemet via de vanliga kanalerna.

### Felmeddelandet &quot;Verifiera din e-postadress&quot; på Magento-kontosidan {#verify-email-address}

Du kan inte skicka in en supportanmälan om du får *Verifiera din e-postadress* liknande det som finns nedan på [Magento-kontosida](https://account.magento.com/).

![Verify_Email_Address_Error](assets/Verify_Email_Address_Error.png){width="800"}

Lösningen är att validera din e-postadress:

1. Klicka på **Validera e-post** knappen under fältet E-post på [Redigera kontoinformation](https://account.magento.com/customer/account/edit/) sida som liknar den nedan.

   ![Validate_Email_Solution](assets/Validate_Email_Solution.png){width="800"}

1. Klicka på **Validera e-post** skickar ett e-postmeddelande till den e-postadress som är registrerad för det här Magento-kontot med en länk för att validera e-postadressen.
1. Klicka på länken för e-postvalidering för att validera din e-post och lösa problemet.
1. Om du inte får något e-postmeddelande med en e-postvalideringslänk skickar du ett e-postmeddelande [Hjälpcentrets inloggningsproblem](mailto:grp-magento-helpcenterloginissues@adobe.com) och ange att du inte kan validera din e-postadress.

>[!NOTE]
>
>Detta gäller endast för e-postvalideringslänken från https://account.magento.com (Magento-kontosida).

### Formulär för att skicka biljetter: handlaren visas inte i den nedrullningsbara listan Organisation {#merchant-not-displayed}

#### Problem

<span class="wysiwyg-underline">Förutsättningar</span>: du har ett konto för delad åtkomst som beviljats av en handlare.

<span class="wysiwyg-underline">Steg som ska återskapas</span>:

1. Logga in på Help Center med ditt delade konto.
1. Klicka på **Skicka en biljett** länk. Formuläret för anmälan av biljett öppnas.
1. Expandera **Organisation** nedrullningsbart fält för att välja handlare.

<span class="wysiwyg-underline">Förväntat resultat</span>:

Handlaren som motsvarar det delade kontot finns i listan **Organisation** alternativ.

<span class="wysiwyg-underline">Faktiskt resultat</span>:

Handlaren som motsvarar det använda delade kontot är inte tillgänglig i **Organisation** alternativ.

#### Lösning

Efter att ha beviljats delad åtkomst från handlaren måste du vidta följande åtgärder (endast en gång):

1. Logga in på [Magento-konto på magento.com webbplats](https://account.magento.com/).
1. I **Byt konto** i det nedrullningsbara fältet längst upp till höger väljer du kontot för delad åtkomst.
1. Klicka på **Support** i den vänstra panelen. På så sätt ser du till att Adobe Commerce Help Center är korrekt konfigurerad via SSO-anropet från Magento.com till Adobe Commerce Help Center.

Om du redan har gjort det kontrollerar du om du har beviljats *delad åtkomst från mer än en handlare* genom att klicka på [[!UICONTROL Shared with me] fliken på ditt konto](https://account.magento.com/grantor/manage/shared/):
* Om bara en [!UICONTROL Share Name] är listad, dvs. du endast har beviljats av en handlare, *du inte ser [!UICONTROL Organization] nedrullningsbar*.
* Om det finns flera [!UICONTROL Share Names], kan handlarens stödrättigheter ha gått ut eftersom licensen tidigare återkallats på grund av betalningsproblem.

### Spåra era biljetter {#track-tickets}

Det är biljetter du får:

* har lämnat in personuppgifter
* har lagts till som bevakare via en CC (kopia)

#### Visa dina biljetter

Om du vill visa alla biljetter klickar du på din profilmeny (det övre högra hörnet) på startsidan för Help Center och väljer **Mina biljetter**.

![diskkritisk varning](assets/my-tickets-8.png){width-&quot;800&quot;}

Klicka på motsvarande flik för att växla mellan dina biljetter och de biljetter du har fått en kopia av:

* **Mina biljetter**
* **Biljetter som jag är CC&#39;d on**
* **Organisationsbiljetter** (tillgängligt om ditt konto är kopplat till flera organisationer)

![hc_my-tickets_tabs.png](assets/hc_my-tickets_tabs.png)

Sortera biljetter genom att klicka **Skapad** eller **Senaste aktivitet** kolumnrubriker.

#### Sök efter biljetter

Om du vill hitta biljetter skriver du sökfrågan i dialogrutan **Sök biljetter** fält och tryck *Retur* på tangentbordet. Välj [en status](#ticket-status) för ytterligare filtrering.

![hc_search-tickets.png](assets/hc_search-tickets.png)

#### Följ organisationsbiljetter

Du kan följa de supportärenden som lämnats in av medlemmarna i din organisation.

När ni följer era organisationsbiljetter kan ni

* kan visa biljetter i **Organisationsbiljetter** tab
* får e-postmeddelanden när nya biljetter skickas eller när befintliga biljetter ändras

Så här följer/avanmäler du biljetter till en organisation:

1. Gå till **Mina biljetter** > **Organisationsbiljetter** -fliken.
1. Välj en organisation på menyn och klicka på **Följ/ångra**.

![hc_follow-org-tickets.png](assets/hc_follow-org-tickets.png)

### Adobe Commerce P1 hotline {#P1-hotline}

**Inloggning krävs** för att komma åt [Adobe Commerce P1 hotline](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html) i vilken det finns P1-hotline-nummer för Adobe Commerce när man behöver hjälp vid en P1-incident och vilka uppgifter som ska lämnas.

### Operativmodellen Adobe Commerce Shared Responsibility {#shared-responsibility-operational-model}

**Inloggning krävs** för att komma åt [Operativmodellen Adobe Commerce Shared Responsibility](https://support.magento.com/hc/en-us/articles/4407700678669) artikel som syftar till att klargöra det operativa ansvaret runt Adobe Commerce endast i fråga om vårt infrastrukturerbjudande.

### Förklaring av supportbiljettfält {#ticket-fields-explained}

#### Berörd URL

Länk till den miljö där Adobe Commerce supportteam skulle kunna se ditt problem. Var noga med att starta URL:en med &quot;http://&quot; eller &quot;https://&quot;.

#### Bifogade filer

Bifoga loggar, skärmdumpar, videoinspelningar eller andra medier som bättre kan illustrera ditt problem.

#### URL för backoffice (endast MOM)

URL:en måste börja med &quot;https://&quot;. Det har vanligtvis formatet: handlarnamn +&quot;.mcom.magento.com/admin/login&quot;, till exempel&quot;https://luma.mcom.magento.com/admin/login&quot;.

Du kan också lägga den direkta länken för ditt problem.

#### CC

E-post till de personer som du vill följa efter din biljett (till exempel *first@e.mail*).

Du får lägga till e-post till personer som inte har ett Magento-konto eller ett Zendesk-konto. Dessa personer kan fortfarande delta i samtalet i din biljett.

Så här lägger du till flera e-postmeddelanden till CC:

>[!NOTE]
>
>Användaren i CC: måste ha ett befintligt konto på https://account.magento.com. Annars måste de först skapa en på https://account.adobe.com och logga in på https://account.magento.com med det kontot.

1. Ange e-postadressen.
1. Tryck *Blanksteg* på tangentbordet för att spara det angivna e-postmeddelandet. E-postmeddelandet visas i en grå ram.\
   ![hc_cc_emails.png](assets/hc_cc_emails.png)
1. Börja skriva nästa e-postmeddelande.
1. Spara alla andra e-postmeddelanden genom att trycka på *Blanksteg*.

Så här tar du bort e-postmeddelanden från CC: klicka **x** i ett rammejl.

![hc_cc_emails_remove.png](assets/hc_cc_emails_remove.png)

#### Produkt

Välj den typ av Adobe Commerce-produkt du arbetar med:

* Adobe Commerce: **[!UICONTROL Implementation Type]** fältet visas när du har valt det här alternativet (se nedan för mer information)
* Magento Order Management
* Adobe Commerce Reporting: Inkluderar inte [Avancerad rapportering](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html)
* Adobe Commerce [Betalningstjänster](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html)
* Adobe Commerce Services: [Kanalhanteraren](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html) endast

#### Implementeringstyp

Det här fältet visas bara när du har valt **[!UICONTROL Product]** = *Adobe Commerce*

Ange distributionsmetod:

* Cloud: Välj det här bara om du använder Adobe Commerce i molninfrastrukturen
* Lokalt: *Alla självvärdsinstanser och [AWS] molnbaserad värdtjänst* (exkluderar Adobe Commerce i molnet)

#### URL för molnprojekt

Ange URL-adressen för Cloud Console-projektet, till exempel `https://console.adobecommerce.com/<owner-user-name>/<project-ID>`.

En annan metod för att hämta projekt-URL är följande:

1. Logga in på [Cloud Console](https://console.adobecommerce.com).
1. Klicka på lämpligt projekt.
1. Kopiera URL-adressen.

#### Kontaktorsak

Orsaken till kontakten varierar beroende på produkt. Välj den kontaktorsak som passar bäst för de symtom du upplever. Se [Beskrivningar av orsaker till supportärende](/help/faq/general/support-ticket-contact-reason-descriptions.md) om du vill veta mer om vilken kontaktorsak du bör välja.

#### Adobe Commerce Environment ID

Det här fältet visas bara när du har valt **[!UICONTROL Contact Reason]** = *Adobe Commerce Cloud*, följt av **Adobe Commerce Application Contact Reason** = *[!DNL Live Search]*.
Gå till **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]** > **[!UICONTROL SaaS Identifier]** och tillhandahåller *[!UICONTROL Data Space ID]*.

#### (Data) Integrationstyp (endast Adobe Commerce Reporting)

Välj den typ av integrering du har i Adobe Commerce Reporting. Detta hjälper våra tekniker att lösa ditt problem på ett effektivare sätt.

#### Beskrivning

Ta med en översikt över ditt problem med så många detaljer som du tycker är rimligt möjliga.

Ange exakta detaljer, steg som ska reproduceras (förutom Adobe Commerce lokala infrastruktur och molninfrastruktur, där det finns en separat [Steg som ska återskapas](#steps) och symtom på ditt problem eller din förfrågan. Inkludera eventuella berörda SKU:er, relevanta datapunkter och andra relevanta länkar.

#### Miljö (Adobe Commerce i molninfrastruktur, Adobe Commerce lokalt, Adobe Commerce Reporting och Shipping only)

Välj **miljötyp** där du står inför problemet:

* Utveckling (**Integrationsgrenar**)
* Mellanlagring
* Produktion

Läs mer om Adobe Commerce i molninfrastrukturmiljöer i [Pro-arkitektur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) i vår användarhandbok.

#### Antal order som påverkas (endast MOM)

Välj det intervall med order som påverkas.

Det här är en listruta och gäller endast för Orderhanteringsprodukt.

#### Organisation

Ange vilken organisation du vill att din biljett ska kopplas till - om du arbetar med flera organisationer.

Det här fältet visas när ditt konto är kopplat till mer än en organisation.

>[!WARNING]
>
>Du måste se till att du har valt rätt organisation. Om du väljer fel organisation kan en tredje part som inte är relaterad till organisationen se potentiellt känslig och personlig information.

>[!NOTE]
>
>Organisationen kan ändras efter att biljetten har skickats. Följ de här stegen för att ändra organisation.
>
>1. Gå till höger kolumn på biljetten.
>1. Leta upp listrutan för tillgängliga organisationer.
>1. Välj lämplig organisation.
>
>![Organisationslistruta](/help/help-center-guide/help-center/assets/change_org.png)

Dessutom skulle det göra det möjligt för oss att snabbt korsreferera till liknande/duplicerade/relaterade biljetter som skickats in för den här organisationen tidigare och identifiera ledtrådar som kan hjälpa till att utreda och lösa den aktuella biljetten.

Om du har delad åtkomst till flera organisationer men det här fältet inte är tillgängligt läser du [Formulär för att skicka biljetter: handlaren visas inte i den nedrullningsbara listan Organisation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#merchant-not-displayed)

#### Partnernamn (handelsnamn)

För handlare: **Partnernamn** är namnet på utvecklingsorganisationen (Adobe Commerce) [Technology Partner](https://partners.magento.com/portal/directory/?&amp;partner_type=6) eller [Solution Partner](https://partners.magento.com/portal/directory/?&amp;partner_type=1)) som deltar i utvecklingen av Adobe Commerce Store.

För partners: **Affärsnamn** är namnet på din kund.

#### Projekt-URL (endast Commerce Cloud)

Länka till [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

#### Steg för återgivning (endast Adobe Commerce lokalt och Adobe Commerce på molninfrastruktur)

Ge exakta steg-för-steg-instruktioner för att återskapa problemet, inklusive:

* Steg som ska replikeras
* Förväntat resultat
* Faktiskt resultat

*Rekommendation:* Anta att du skriver dessa steg för någon som vet **ingenting** om Adobe Commerce:

* Alla steg ska nämnas, även om det verkar enkelt och uppenbart
* Förlita dig inte på att din läsare vet vad du menar

Skriv på enkelt språk, med korta meningar.

#### Ämne

Ta med en kort översikt över ditt problem (till exempel *Fel 404 på alla sidor* ).

**Föreslagna artiklar:** När du anger söktermen visas en lista med Adobe Commerce-dokumentationsartiklar som kan vara relaterade till ditt problem. Klicka på en artikel i listan för att öppna den.

![hc_subject-föreslagen-articles.png](assets/hc_subject-suggested-articles.png)

*Rekommendation:* Ta en titt på de föreslagna artiklarna, de kan innehålla den lösning du förväntar dig av Adobe Commerce supportteam.

#### Version (endast Adobe Commerce lokalt, Adobe Commerce om molninfrastruktur och leverans)

Välj den Adobe Commerce-version som du vill ha hjälp med. Alla versioner av Adobe Commerce som stöds visas överst. Versioner som inte stöds visas längst ned med parenteser. Om du håller på att migrera bör du välja den senaste versionen för att vara säker på att du stöds.

Om du vill hitta versionen av din Adobe Commerce (molninfrastruktur) bläddrar du nedåt i [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) och kontrollera fönstrets nedre mitt.

![Kontaktorsak inställd på Adobe Commerce Cloud-program och Adobe Commerce Application Contact Reason inställd på Live Search](assets/magento-env-id.png)

Om du använder [Elasticsearch](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/search-engine/overview.html) eller [OpenSearch](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/search-engine/aws-opensearch.html)markerar du inte det här alternativet.

Om du vill ha den här informationen går du till Adobe Commerce Admin **Marknadsföring** > **Live Search** > **GraphQL Playground**, rulla nedåt till sidans nederkant och klicka sedan på **HTTP-SIDHUVUDEN**.

### Biljettstatus: Hur biljetter behandlas {#ticket-status}

Din biljett kan ha någon av dessa tre statusar.

#### **1. Öppna**

Biljetten är inte löst och behandlas av Adobe Commerce supportteam. När du har angett all information som du förväntar dig i ett visst steg i konversationen och nästa steg måste tas av Adobe Commerce support, har din biljett **Öppna** status.

#### **2. Väntar på ditt svar**

Adobe Commerce support förväntar sig information från dig.

I ditt svar kan du ange ytterligare teknisk information om ditt problem, ange eskaleringsinformation eller ange om lösningen som Adobe Commerce support erbjuder har visat sig vara till hjälp för ditt problem. Se till att du anger dina svar så fort du kan eftersom Adobe Commerce support inte kan fortsätta att behandla din biljett när den finns i **Väntar på ditt svar** status.

Referera till [Uppdatering av Adobe Commerce supportavtal för biljettlivscykelpolicy](/help/help-center-guide/help-center/magento-support-ticket-lifecycle-policy-update.md) artikel om du vill ha information om timing och meddelandepolicy.

#### **3. Löst**

Adobe Commerce support har gett en lösning på ditt problem och du har gått med på att den har varit till hjälp. Det är du som markerar biljetten som **Löst**. Om det åtgärdade problemet inträffar igen kan du öppna biljetten igen och ange dess status till tillbaka **Öppna**.

### Samtal i din biljett {#conversation-in-ticket}

Samtal i biljetten innehåller alla kommentarer som skrivits av dig eller Adobe Commerce supportteam. Kommentarerna visas från den senaste (överst) till den tidigaste (nederst).

Gör så här om du vill lägga till en kommentar i konversationen:

1. Rulla längst ned på biljetten.
1. Klicka på **Lägg till i konversation** fält för att börja skriva.

   ![hc_add-to-console.png](assets/hc_add-to-conversation.png)

1. Om du vill lägga till en person i kommentaren anger du e-postadressen i **CC** kommentarsfältets fält.
   >[!NOTE]
   >
   >Användaren i CC: måste ha ett befintligt konto på https://account.magento.com. Annars måste de först skapa en på https://account.adobe.com och logga in på https://account.magento.com med det kontot.

   ![hc_console-write.png](assets/hc_conversation-write.png)

1. När du är klar med kommentaren klickar du **Skicka**.

### Lös din biljett {#resolve-ticket}

Lös din biljett genom att klicka **Markera som löst** längst ned på biljetten.

### Öppna en uppföljningsbiljett {#follow-up}

Genom att öppna en uppföljningsbiljett säkerställs att den ursprungliga utgåvan är länkad till uppföljningsbiljetten för kontinuitet.

Om du vill öppna en uppföljningsbiljett klickar du på&#x200B;*skapa en uppföljning*&quot; längst ned på biljetten som du vill göra en uppföljning till.

## DELAD ÅTKOMST: BEVILJA ÅTKOMST TILL DITT KONTO FÖR ANDRA ANVÄNDARE {#shared-access}

Du kan ge andra kontoinnehavare på Magento begränsad åtkomst till ditt konto. I synnerhet använder **delad åtkomst** kan du ge betrodda anställda och tjänsteleverantörer behörighet att använda ditt Help Center-konto så att de kan arbeta med dina supportärenden.

Du kan ange och hantera delad åtkomst via kontosidan på Magento [https://account.magento.com](https://account.magento.com/).

### Vem kan ge delad åtkomst? {#who-can-provide-shared-access}

Det är bara kontoägaren (primär kontoinnehavare) som har behörighet att ge delad åtkomst för andra användare.

Det är kundens ansvar att hantera användare och deras åtkomst, särskilt när det gäller delad åtkomst. Adobe Commerce supportteam kan alltså inte ge delad åtkomst till ett Magento-konto åt en kund. Kunderna uppmuntras att lägga till användare med delad åtkomst själva med hjälp av [Magento-kontosida](https://account.magento.com/).

Användare som har fått delad åtkomst kan inte överföra eller ge sådan åtkomst till andra användare.

### Ge delad åtkomst {#provide-shared-access}

Se [Dela ditt konto](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) i Adobe Commerce användarhandbok för mer information om hur du skapar ett delat konto.

När en ny användare har fått delad åtkomst är den relaterade informationen tillgänglig i **Delad åtkomst** > **Hantera behörigheter** på Magento-kontosidan.

![magento-account-shared-manage-permissions](assets/magento-account-shared-manage-permissions.png){width="800"}

### Återkalla (ta bort) delad åtkomst {#revoke-shared-access}

1. Logga in på ditt Magento-konto på [https://account.magento.com](https://account.magento.com/).
1. Välj under Delad åtkomst på panelen till vänster **Hantera behörigheter.**
1. Hitta användaren som den delade åtkomsten ska återkallas från och klicka på ![ta bort ikon](assets/remove_icon.png){width="25"} i användarens rad (**Åtgärder** kolumn).
1. Klicka **Ta bort användare** för att återkalla åtkomst eller X i det övre hörnet för att avbryta återkallandet.

   ![revoke_shared_access](assets/revoke_shared_access.png){width="800"}

   Du kan också återkalla delad åtkomst med **Redigera** meny:

1. Logga in på ditt Magento-konto på [https://account.magento.com](https://account.magento.com/).
1. Välj under Delad åtkomst på panelen till vänster **Hantera behörigheter.**
1. Hitta användaren som den delade åtkomsten ska återkallas från och klicka på **Redigera** i användarens rad (**Åtgärder** kolumn).
1. Klicka **Ta bort den här användaren** längst ned på sidan.
1. Klicka på **Ta bort användare** för att återkalla åtkomst eller X i det övre hörnet för att avbryta återkallandet.

### Hur tar jag bort användare som beviljats delad åtkomst via ett Cloud-projekt? {#remove-cloud-shared-access-users}

<u>Berörda produkter och versioner</u>

* Adobe Commerce Cloud (alla versioner)

<u>Orsak</u>

Om du har/har haft ett Adobe Commerce Cloud-projekt och lagt till en användare i projektet, skulle de automatiskt ha fått delad åtkomst på projektägarens MAGE-ID. Detta anges normalt i **[!UICONTROL Share Name]** kolumn, visa *Delad åtkomst i molnet från MAG[XYZ]*.

Om länken DELETE saknas innebär det att delad åtkomst automatiskt beviljades via Commerce Cloud.

<u>Lösning</u>

Det går inte att ta bort listan över användare med delad åtkomst med resursnamnet *Delad åtkomst i molnet från MAG[XYZ]* om den delade åtkomsten inte har lagts till/getts på den här sidan. Dessa bevaras i informations-/revisionssyfte.

När du har återkallat behörigheten för dessa användare med delad åtkomst har de inte längre den åtkomsten.

1. Logga in på ditt Magento-konto på [https://account.magento.com](https://account.magento.com/).
1. På panelen till vänster, under *[!UICONTROL Shared Access]*, välja **[!UICONTROL Manage Permissions]**.
1. Hitta användaren som den delade åtkomsten ska återkallas från och klicka på **[!UICONTROL Edit]** i användarens rad (*[!UICONTROL Actions]* kolumn).
1. Avmarkera alla resurser under *[!UICONTROL Grant Account Permissions]*.

![grant-account-permissions-image](assets/help-center-user-guide-grant-account-permissions-image.png){width="800"}

Mer information finns i [Hantera användaråtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-project-web-interface) dokumentation om vår Commerce om Cloud Infrastructure Guide.

### Åtkomst till delat konto (växlingskonton) {#switch-accounts}

Följ de här stegen för att använda den delade åtkomst du fått:

1. Logga in på ditt Magento-konto på [https://account.magento.com](https://account.magento.com/).
1. Klicka på **Byt konto** och välj ett konto.

   ![magento-account-shared-switch](assets/magento-account-shared-switch.png){width="800"}

Om du vill veta vilket konto du använder (ditt eget hemkonto eller delad åtkomst) kan du läsa **Byt konto** meny: den visar det aktiva kontot.

### Felsökning av delad åtkomst {#troubleshooting-shared-access}

Läs mer i [Felsökningsartikel för delad åtkomst](/help/troubleshooting/miscellaneous/shared-access-troubleshooting.md) i vår kunskapsbas för support.

## FAKTURERINGSFRÅGOR FÖR ADOBE COMMERCE {#billing-faq}

Handlare betalar vanligtvis för våra tjänster via en kreditkortstransaktion (CC), och detta [Frågor och svar om fakturering för Adobe Commerce](/help/faq/general/billing-faq-for-adobe-commerce.md) är en resurs som hjälper dig att betala din räkning.

## MAGENTO U ÄR NU EN DEL AV ADOBE DIGITALA LÄRNINGSTJÄNSTER {#magento-u}

Magento U har slagits samman med [Adobe Digital Learning Services (ADLS)](https://learning.adobe.com/).

Magento U Zendesk kommer att fasas ut.
