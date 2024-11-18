---
title: Adobe Commerce Support Knowledge Base
description: Allt du behöver veta för att felsöka och underhålla din Commerce Store.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 52d07e5a5bb7be492f6799d0e5ad9fd49c3a61ae
workflow-type: tm+mt
source-wordcount: '1074'
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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25234">Licensöverföring på grund av omstrukturering:</a> Den här artikeln hjälper dig att enkelt övergå till ditt Adobe Commerce-konto, inklusive alla nödvändiga steg som krävs för att hålla igång dina tjänster utan problem.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25289">Säkerhetsuppdateringar för Adobe Commerce (APSB24-90):</a> Den 12 november 2024 släppte Adobe en säkerhetsuppdatering för Adobe Commerce (i molnet och lokalt) och Magento Open Source-funktioner som drivs av Commerce Services och distribueras som SaaS (Software as a Service). Uppdateringen åtgärdar en säkerhetslucka som klassas som <a href="https://helpx.adobe.com/security/severity-ratings.html">critical</a>. 
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25231">MageID-kontoägaren kan inte logga in och skicka en supportanmälan:</a> Den här artikeln åtgärdar Adobe Commerce-problemet där du inte kan logga in på ditt konto (MageID) på account.magento.com för att skicka en supportanmälan.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25135">OTB-tillägget Braintree för Adobe Commerce saknar stöd för de senaste Visa 3DS-fälten:</a> I den här artikeln beskrivs hur du följer de nya Visa-reglerna eftersom Adobe Commerce färdiga Braintree-tillägg saknar stöd för de senaste Visa 3DS-fälten.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61528-retrieving-roles-using-graphql-returns-no-results">ACSD-61528: Hämtning av roller med GraphQL returnerar inga resultat:</a> Korrigeringen ACSD-61528 åtgärdar ett problem där hämtning av roller från företagets administratör med GraphQL alltid returnerar ett null-resultat. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.53 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-48318-environment-emulation-nesting-error-in-system-log">ACSD-48318: Fel vid kapsling av miljöemulering i system.log:</a> Korrigeringen ACSD-48318 åtgärdar ett fel där felmeddelandet <em>main.ERROR:Environment emulation nesting inte tillåts</em> i <code>system.log</code> varje gång ett fakturameddelande skickas. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.53 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59366-delete-teams-with-deactivated-users-not-visible-in-the-team-list">ACSD-59366: Ta bort team med inaktiverade användare som inte visas i grupplistan:</a> Korrigeringen ACSD-59366 åtgärdar ett problem där ett fel inträffar när du försöker ta bort ett team som innehåller inaktiverade användare som inte visas i grupplistan. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.52 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60234-paypal-shows-an-incorrect-amount-when-discount-is-applied">ACSD-60234: PayPal visar ett felaktigt belopp när rabatten tillämpas:</a> Korrigeringsfilen ACSD-60234 åtgärdar problemet där [!DNL PayPal] visar ett felaktigt belopp när rabatten tillämpas via betalningsmetoden. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.51 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60673-cart-price-rule-fix-for-multiple-payment-methods-at-checkout">ACSD-60673: Problem med kundprisregel som har korrigerats för flera betalningsmetoder vid utcheckning:</a> Korrigeringsfilen ACSD-60673 åtgärdar ett problem där rabatterna från en [!UICONTROL Cart Price Rule] som använder ett betalningsmetodvillkor inte alltid anges i summorna. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.52 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60584-access-token-created-for-one-website-is-allowed-to-access-information-on-other-websites">ACSD-60584: Åtkomsttoken som skapats för en webbplats har åtkomst till information på andra webbplatser:</a> Korrigeringen för ACSD-60584 åtgärdar ett problem där den åtkomsttoken som skapats för användaren på en webbplats har åtkomst till eller kan ändra kundinformation på andra webbplatser. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.53 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60788-fixes-issue-where-custom-scripts-for-google-tag-manager-are-not-executed-due-to-content-security-policy-errors">ACSD-60788: Anpassade skript för Google Tag Manager körs inte på grund av säkerhetsfel för innehåll:</a> Korrigeringsfilen ACSD-60788 åtgärdar ett problem där anpassade skript för [!DNL Google Tag Manager] inte körs på grund av fel i säkerhetsprincipen för innehåll. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.52 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61366-setup-command-fails-with-error">ACSD-61366: Kommandot <code>bin/magento setup:static-content:deploy --jobs 4</code> påträffar flera jobbfel med ett fel:</a> Korrigeringsfilen ACSD-61366 åtgärdar ett problem där kommandot <code>bin/magento setup:static-content:deploy --jobs 4</code> påträffar flera jobbfel med porten <em>Port måste konfigureras inom värdparametern</em> trots att porten för databasanslutningen anges. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.52 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60816-newrelic-browser-monitoring-scripts-injected-by-apm-agent-are-not-compliant-with-csp">ACSD-60816: Skript för webbläsarövervakning i New Relic som har injicerats av APM-agenten är inte kompatibla med CSP:</a> Korrigeringsfilen ACSD-60816 åtgärdar ett problem där de [!DNL New Relic] skript för webbläsarövervakning som har injicerats av APM-agenten inte följer Content Security Policy (CSP). Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.51 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59952-error-on-deleting-shared-catalog-with-same-group-id-as-another-shared-catalog">ACSD-59952: Fel vid borttagning av delad katalog med samma grupp-ID som en annan delad katalog:</a> Korrigeringen ACSD-59952 åtgärdar det fel som uppstod när delade kataloger med samma <code>customer_group_id</code> som en annan delad katalog togs bort. Dessutom förhindras användare från att skapa sådana delade kataloger. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.52 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59786-graphql-returns-an-error-when-fetching-a-quote-id-for-an-expired-quote">ACSD-59786: GraphQL returnerar ett fel när en <code>quote_id</code> hämtas för en offert som har gått ut:</a> Korrigeringen ACSD-59786 åtgärdar ett problem där en GraphQL-fråga returnerar ett fel när en <code>quote_id</code> för en offert som har gått ut hämtas. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.51 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59967-javascript-error-prevents-google-maps-from-rendering-correctly">ACSD-59967: JavaScript-fel förhindrar att Google Maps återges korrekt:</a> Korrigeringsfilen ACSD-59967 åtgärdar ett problem där JavaScript-felet förhindrar att [!DNL Google Maps] återges korrekt. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.51 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-59930-improves-performance-of-company-flows">ACSD-59930: Förbättrar prestanda för företagets flöden:</a> Korrigeringsfilen ACSD-59930 åtgärdar ett problem där ett <em>Timeout</em> -fel visas på administratörspanelen när ett företag med en administratör som har fler än 1 000 adresser skapas, sparas eller tas bort. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.53 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>14 november 2024</td>
  </tr>
</table>
