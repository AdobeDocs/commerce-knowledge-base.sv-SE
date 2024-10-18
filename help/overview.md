---
title: Adobe Commerce Support Knowledge Base
description: Allt du behöver veta för att felsöka och underhålla din Commerce Store.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 607b835da518536196654734f62d78d095099476
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 0%

---

# Adobe Commerce Support Knowledge Base

>[!NOTE]
>
>Adobe Commerce Support Knowledge Base Guide kommer snart att struktureras om och innehållet flyttas till andra platser i Adobe Experience League. Under tiden kommer vi att fortsätta att underhålla och uppdatera innehållet i den här guiden.

![Knowledge Base-startsida](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

Informationen i den här kunskapsbasen kompletterar [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs), [Adobe Commerce Merchant Guide](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) och andra Adobe Commerce-publikationer. Här beskrivs felsökning och bästa praxis, vardagsmeddelanden, svar på vanliga frågor och svar samt specifika scenarier som inte har omnämnts (av någon anledning) i den officiella dokumentationen.

## Vad finns det i den här kunskapsbasen?

| KATEGORI | BESKRIVNING |
| --- | --- |
| [Supportverktyg](/help/support-tools/overview.md) | Förbättra e-handelsupplevelsen med Adobe Commerce olika supportverktyg. Vi erbjuder personaliserade, bästa praxis, verktyg för diagnostik och övervakning samt den mest relevanta informationen om er webbplats. |
| [Meddelanden](/help/announcements/overview.md) | Få viktiga uppdateringar från Adobe Commerce-teamen. |
| [Felsökning](/help/troubleshooting/overview.md) | Få självbetjäningslösningar och patchar från Adobe Commerce supportteam. |
| [Användarhandbok för Help Center](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Lär dig hur du hanterar supportärenden, ger delad åtkomst och bläddrar effektivt i kunskapsbasen. |
| [Instruktioner](/help/how-to/overview.md) | Få tydliga stegvisa instruktioner från Adobe Commerce supportteam. |
| [Vanliga frågor](/help/faq/overview.md) | Frågor och svar om Adobe Commerce policyer, strategier och information om Adobe Commerce funktioner. |

## Nyheter

<table style="width:100%">
  <tr>
    <th style="width:70%">Beskrivning</th>
    <th style="width:15%">Typ</th>
    <th style="width:15%">Datum</th>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25075">Verktyget för säkerhetsgenomsökning returnerar"Kan inte avgöra om servern använder 2FA":</a> Kontrollera om modulen <code>Magento_TwoFactorAuth</code> har inaktiverats för att åtgärda felet. För att kontrollen ska lyckas bör den i allmänhet vara aktiverad.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60632-address-saved-on-every-order-attempt">ACSD-60632: Adress sparad med varje orderförsök:</a> Korrigeringsfilen ACSD-60632 åtgärdar ett problem där en ny adress sparas med varje orderplaceringsförsök, oavsett om ordern har skapats eller inte. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.51 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60326-graphql-query-error-customer-return-status">ACSD-60326: GraphQL-fråga om kundreturstatus ger ett fel:</a> Korrigeringsfilen ACSD-60326 åtgärdar ett problem där ett fel inträffar i GraphQL-frågan om kundreturstatus. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.51 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59925-sorting-items-in-media-gallery">ACSD-59925: Sortering av objekt i mediegalleriet efter position i GraphQL:</a> Korrigeringen ACSD-59925 åtgärdar ett problem där objekt i mediegalleriet inte sorteras efter position, vilket leder till en felaktig visningsordning. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.52 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61322-products-not-assigned-to-shared-catalogue">ACSD-61322: Produkter som inte har tilldelats den delade katalogen ingår i XML-webbplatskartan:</a> Korrigeringen ACSD-61322 åtgärdar ett problem där produkter/kategorier som inte har tilldelats den delade katalogen för standardgruppen (Allmänt) fortfarande ingår i XML-platskartan. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.52 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60590-optimized-bestseller-report-generation">ACSD-60590: Förbättrade prestanda för Bestsellers Aggregated Daily Report-generering:</a> Korrigeringen ACSD-60590 åtgärdar ett problem där det tar lång tid för Bestsellers Aggregated Daily Report att generera för ett stort antal placerade order. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.52 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59865-cart-price-rule-fix-for-insufficient-quantity-issue">ACSD-59865: Prisregeln för kundvagn kan inte avbryta tidigare regler på grund av otillräcklig produktkvantitet:</a> Korrigeringen ACSD-59865 åtgärdar ett problem där värdet för <em>Rabattkvantitet i </em> i <em>Fast beloppsrabatt</em>, <em>Procent av produktprisrabatt</em> och <em>Köp X - köp </em> Kundprisreglerna avbryter inte längre åtgärden för tidigare regler. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.52 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/error-when-filtering-orders-in-admin">Fel vid filtrering av order i Admin:</a> Den här artikeln innehåller en korrigering för Adobe Commerce-problemet där ett fel inträffar när försök görs att filtrera ordningarna i Admin efter datum. Meddelandet <em>Överträdelse av integritetsbegränsning: 1052 Kolumnen 'created_at' där satsen är tvetydig</em> visas.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25030">Adobe Commerce: Inline JavaScript Issues on checkout page in Content Security Policy (CSP) restricted mode (Inline Issues on checkout page):</a> Den här artikeln innehåller detaljerade förklaringar och lösningar för problem som uppstår med anpassade JavaScript som har lagts till via Adobe Commerce Admin och Google Tag Manager i Adobe Commerce 2.4.7 vid utcheckning när <strong>begränsat CSP-läge</strong> är aktiverat.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-61195-empty-cart-on-final-graphql-page">ACSD-61195: Cart GraphQL-begäran returnerar inte objekt på den sista sidan:</a> Korrigeringen ACSD-61195 åtgärdar ett problem där inga varukorgsobjekt returneras på den sista sidan för kundvagnsbegäran från GraphQL. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.51 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-59514-forms-in-admin-with-page-builder-throw-error-in-browser-console">ACSD-59514: Forms i Admin med Page Builder returnerar ett fel i webbläsarkonsolen:</a> Korrigeringsfilen ACSD-59514 åtgärdar ett problem där formulären i Admin med Page Builder orsakade felet <em>Page Builder återgav i 5 sekunder utan att frigöra lås</em> i webbläsarkonsolen efter att formuläret har skickats och ändringarna kan inte sparas . Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.50 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60538-if-product-is-disabled-attributes-dont-show">ACSD-60538: Attribut visas inte korrekt om produkten är inaktiverad i <em>Alla butiksvyer</em>:</a> Korrigeringen ACSD-60538 åtgärdar ett problem där produktattributen inte visas korrekt i GraphQL-svaret om en produkt är inaktiverad i <em>Alla butiksvyer</em> och endast aktiveras i specifika butiksvyområden. som leder till att produkten inte visas som den ska. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.51 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-58352-return-attribute-labels-for-the-default-store-are-returned-via-graphql-api">ACSD-58352: Returattributetiketter för standardbutiken returneras via GraphQL API:</a> Korrigeringsfilen ACSD-58352 åtgärdar ett problem där returattributetiketter för standardbutiken returneras via GraphQL API när en icke-standardbutiksvy anges i begärandehuvudet. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.50 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-24983">Listrutan <em>Byt konto</em> saknas i ditt konto:</a> Den här artikeln innehåller en lösning på Adobe Commerce-problemet där listrutan <em>Byt konto</em> saknas i ditt konto och du har förlorat åtkomsten att skicka biljetter för handlarens räkning.
    </td>
    <td>Ny artikel</td>
    <td>17 oktober 2024</td>
  </tr>

<tr>  
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-56979-product-images-removed-after-staging-update-deleted">ACSD-56979: Produktbilder som tagits bort efter borttagning av mellanlagringsuppdatering:</a> Korrigeringen ACSD-56979 åtgärdar ett problem där produktbilder tas bort efter borttagning av en mellanlagringsuppdatering. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.49 har installerats.  
    </td>
    <td>Ny artikel</td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-48210-store-view-specific-scope-attribute-overrides-global-values">ACSD-48210: Butiksvyspecifika omfångsattribut åsidosätter globala värden:</a> Korrigeringsfilen ACSD-48210 åtgärdar ett problem där attributen i det globala omfånget åsidosätts när ett <em>Webbplatsomfångsattribut </em> uppdateras i en viss butiksvy. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.50 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-59280-fix-for-reflection-union-type-error">ACSD-59280: ReflectionUnionType::getName()-fel i 2.4.4-pX-installationer:</a> Korrigeringen ACSD-59280 åtgärdar ett problem där anropet till den odefinierade metoden <code>ReflectionUnionType::getName()</code> inträffar under installationen av 2.4.4-pX-versioner. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.50 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-54887-customer-shopping-cart-gets-cleared-after-session-expiry">ACSD-54887: Kundvagnen raderas efter att kundsessionen har upphört:</a> Korrigeringsfilen ACSD-54887 åtgärdar ett problem där kundens kundvagn raderas efter att kundsessionen har upphört och <em>Beständig kundvagn</em> är aktiverad. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.50 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-60303-admin-order-placement-fix">ACSD-60303: Problem med placering av administratörsorder som har aktiverats med HTML-minification:</a> Korrigeringen ACSD-60303 åtgärdar ett problem där en beställning från Admin inte kan placeras om HTML-minification är aktiverat. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.50 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57045-url-rewrites-cause-infinite-page-looping-after-website-root-unchecked-hierarchy">ACSD-57045: URL-omskrivningar orsakar oändliga sidloopar efter <em>webbplatsens rot</em> avmarkerad från hierarki:</a> Korrigeringen ACSD-57045 åtgärdar ett problem där URL-omskrivningar orsakar oändliga sidloopar efter att <em>webbplatsens rot</em> har avmarkerats från hierarkin. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.49 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/ascd-58446-deleting-a-team-with-child-users-or-teams-via-graphql-gives-an-uninformative-error-message">ACSD-58446: Om du tar bort ett team med underordnade användare eller team via GraphQL får du ett felmeddelande som inte ger information:</a> Korrigeringen ACSD-58446 åtgärdar Adobe Commerce-problemet där ett team med underordnade användare eller team via GraphQL returnerar ett felmeddelande som inte ger information och som inte stämmer överens med användargränssnittet. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.49 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-58375-wrong-youtube-api-key-configuration-causes-an-error-when-adding-a-youtube-video-at-the-store-view-level">ACSD-58735: Felaktigt konfigurerad YouTube API-nyckel orsakar fel när video läggs till på butiksvynivå:</a> Korrigeringen ACSD-58735 åtgärdar ett problem där fel YouTube API-nyckelkonfiguration orsakar ett fel när en YouTube-video läggs till på butiksvynivå. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.49 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57086-orders-placed-from-non-default-websites-with-terms-conditions-processed-incorrectly">ACSD-57086: Order från icke-standardwebbplatser med villkor aktiverade behandlas felaktigt:</a> Korrigeringsfilen ACSD-57086 åtgärdar ett problem där beställningar från icke-standardwebbplatser med villkor aktiverade inte behandlas korrekt. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.49 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58141-phpsessid-regenerates-on-post-requests-for-logged-in-customers-with-l2-redis-cache-enabled">ACSD-58141: PHPSESSID återskapar begäranden om POST för inloggade kunder om L2 Redis-cachen är aktiverad:</a> Korrigeringen ACSD-58141 åtgärdar ett problem där PHPSESSID återskapar begäranden om POST till en inloggad kund om L2 Redis-cachen är aktiverad och kunden uppdateras från Admin. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.50 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58790-fixes-pinch-to-zoom-functionality-on-the-product-detail-page-images-in-mobile-view-on-chrome">ACSD-58790: Korrigerar funktionen att fästa vid zoomning på produktinformationssidbilder i mobilvyn i Chrome:</a> Korrigeringen ACSD-58790 åtgärdar Adobe Commerce-problemet där bilden i mobilvyn i Chrome inte zoomade in på bilden som förväntat. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.50 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58442-fixes-issue-devices-768px-mobile-view-instead-desktop">ACSD-58442: Korrigerar problemet där enheter med 768 px bredd behandlas som mobila enheter, vilket gör att meny och rubrik läses in i mobilvyn och inte i skrivbordsvyn:</a> Korrigeringsfilen ACSD-58442 åtgärdar Adobe Commerce-problemet där enheter med en bredd på 768 px hanteras som mobila enheter, vilket gör att menyn och huvudet läses in i mobilvyn i stället för en dator. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.50 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>17 oktober 2024</td>
  </tr>
</table>
