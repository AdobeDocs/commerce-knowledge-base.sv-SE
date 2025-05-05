---
title: Adobe Commerce Support Knowledge Base
description: Allt du behöver veta för att felsöka och underhålla din Commerce Store.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 6d22ea4725249df1528625672be405464b1411e8
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 0%

---

# Adobe Commerce Support Knowledge Base

>[!NOTE]
>
>Adobe Commerce Support Knowledge Base Guide kommer snart att struktureras om och innehållet flyttas till andra platser i Adobe Experience League. Under tiden kommer vi att fortsätta att underhålla och uppdatera innehållet i den här guiden.

![Knowledge Base-startsida](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

Informationen i den här kunskapsbasen kompletterar [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs), [Adobe Commerce Merchant Guide](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html?lang=sv-SE) och andra Adobe Commerce-publikationer. Här beskrivs felsökning och bästa praxis, vardagsmeddelanden, svar på vanliga frågor och svar samt specifika scenarier som inte har omnämnts (av någon anledning) i den officiella dokumentationen.

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
    <a href="https://experienceleague.adobe.com/sv/docs/experience-cloud-kcs/kbarticles/ka-25301">Åtgärda [!DNL New Relic] agentproblem med PHP 8.2-8.3-uppgraderingen i Adobe Commerce:</a> När du uppgraderar PHP från version 8.2 till 8.3 kanske du märker att [!DNL New Relic] Agent slutar fungera i din Adobe Commerce-miljö. Detta problem har observerats i miljöer med staging och produktion. I den här artikeln hittar du steg för att felsöka och lösa problemet.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/experience-cloud-kcs/kbarticles/ka-25321">[!DNL Security Scan Tool] returnerar APSByy-xx-säkerhetsuppdateringar som är tillgängliga även om korrigeringen redan har tillämpats:</a> [!DNL Security Scan Tool] Rapporterar APSByy-xx-säkerhetsuppdateringar som är tillgängliga för Adobe Commerce och Magento Open Source trots att du redan har installerat korrigeringen. Du kan bortse från detta meddelande.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61845-error-occurs-for-requests-with-text-html-accept-header">ACSD-61845: Det uppstod ett fel för begäranden med text/html accept header:</a> Korrigeringsfilen ACSD-61845 åtgärdar ett problem där en HTTP-begäran med endast text/html accept header orsakar ett 500-fel på grund av felmatchningar av medietyper i svarshanteringen. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.54 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61200-fixes-discount-tax-compensation-in-sales-total-calculations">ACSD-61200: Felaktig momskompensation i beräkning av försäljningssumma:</a> Korrigeringen ACSD-61200 åtgärdar ett problem där Rabattskatteutjämningsbelopp och Momskompensationsbelopp saknas i beräkningarna för totalt belopp och totalt belopp, vilket resulterar i diskrepanser mellan försäljningsorderdata och kupongrapportdata. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.54 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61199-cms-page-hierarchy-tab-doesnt-display-proper-tree-structure">ACSD-61199: Fliken [!UICONTROL Hierarchy] på CMS-sidan visar inte rätt trädstruktur:</a> Korrigeringsfilen ACSD-61199 åtgärdar ett fel där fliken [!UICONTROL Hierarchy] på CMS-sidan inte visar en korrekt trädstruktur när du redigerar en CMS-sida med en befintlig hierarki. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.54 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60804-editing-customer-linked-to-deleted-company-causes-error">ACSD-60804: Om du redigerar en kund som är associerad med ett borttaget företag uppstår ett fel:</a> Korrigeringsfilen för ACSD-60804 åtgärdar ett problem där redigering av en kund som är associerad med ett borttaget företag orsakar ett fel <em>Anrop till en medlemsfunktion getSuperUserId() på null</em>. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.53 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61522-email-in-name-fields-sends-invalid-order-confirmations">ACSD-61522: E-postadresser i fälten [!UICONTROL First] och [!UICONTROL Last Name] skickar ogiltiga orderbekräftelser:</a> Korrigeringen ACSD-61522 åtgärdar problemet där det går att ange e-postadresser i en gästkunds fält [!UICONTROL First Name] och [!UICONTROL Last Name] vilket leder till att ogiltiga orderbekräftelsemeddelanden skickas. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.54 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-62485-async-operations-all-consumer-stops-working-when-company-is-created">ACSD-62485: <code>async.operations.all</code> Konsumenten slutar att arbeta när företaget skapas:</a> Korrigeringsfilen ACSD-62485 åtgärdar ett problem där <code>async.operations.all</code> konsumenten slutar arbeta när ett B2B-företag skapas. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.54 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60684-graphql-product-sorting-by-multiple-fields-does-not-work-as-expected">ACSD-60684: GraphQL produktsortering efter flera fält fungerar inte som väntat:</a> Korrigeringen ACSD-60684 åtgärdar ett problem där GraphQL produktsortering efter flera fält inte fungerar när sorteringen skickas i variabler. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.52 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61553-cart-price-rule-discounts-are-incorrectly-calculated-when-multiple-discounts-with-different-priorities-are-applied">ACSD-61553: [!UICONTROL Cart Price Rule] beräknas felaktigt när flera rabatter med olika prioriteter tillämpas:</a> Korrigeringsfilen ACSD-61553 åtgärdar ett problem där [!UICONTROL Cart Price Rule] beräknas felaktigt när flera rabatter med olika prioriteter tillämpas. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.53 har installerats.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58383-duplicate-credit-memos-from-simultaneous-refund-requests-via-rest-api">ACSD-58383 Adobe Commerce-korrigering: Dubblettkreditnotor från samtidiga återbetalningsbegäranden via REST API:</a> Korrigeringsfilen ACSD-58383 åtgärdar problemet där en återbetalning via REST API med två identiska begäranden som utförs samtidigt resulterar i dubbla kreditnotor. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.55 är installerad.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58471-dynamic-content-fails-load-product-detail-page">ACSD-58471: Det går inte att läsa in dynamiskt innehåll på produktinformationssidan när de associerade katalogprisreglerna var schemalagda:</a> Korrigeringen ACSD-58471 löser problemet där dynamiskt innehåll inte kan läsas in på produktinformationssidan när de associerade katalogprisreglerna var schemalagda. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.55 är installerad.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58735-restricted-admin-cant-view-abandoned-shopping-carts">ACSD-58735: Begränsad administratör kan inte visa övergivna kundvagnar på kundkontot för den associerade webbplatsen:</a> Korrigeringen ACSD-58735 åtgärdar ett problem där en administratörsanvändare med en begränsad roll inte kan visa övergivna kunders kundvagnar från fliken <strong>[!UICONTROL Commerce Admin]</strong> &gt; <strong>[!UICONTROL Reports]</strong> &gt; <strong>[!UICONTROL Abandoned Carts]</strong> &gt; <strong>[!UICONTROL Select Cart]</strong> &gt; <strong>[!UICONTROL Shopping Cart]</strong>. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.55 är installerad.
    </td>
    <td>Ny artikel </td>
    <td>5 december 2024</td>
  </tr>
</table>
