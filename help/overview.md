---
title: Adobe Commerce Support Knowledge Base
description: Allt du behöver veta för att felsöka och underhålla din Commerce Store.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 738a5455267647d294d222d5bb6149254dcb93dd
workflow-type: tm+mt
source-wordcount: '1394'
ht-degree: 0%

---

# Adobe Commerce Support Knowledge Base

![Knowledge Base-startsida](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

Informationen i den här kunskapsbasen kompletterar [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs), [Adobe Commerce Merchant Guide](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) och andra Adobe Commerce-publikationer. Här beskrivs felsökning och bästa praxis, vardagsmeddelanden, svar på vanliga frågor och svar samt specifika scenarier som inte har omnämnts (av någon anledning) i den officiella dokumentationen.

## Vad finns i kunskapsbasen?

| KATEGORI | BESKRIVNING |
| --- | --- |
| [Supportverktyg](/help/support-tools/overview.md) | Förbättra e-handelsupplevelsen med Adobe Commerce olika supportverktyg. Vi erbjuder personaliserade, bästa praxis, verktyg för diagnostik och övervakning samt den mest relevanta informationen om er webbplats. |
| [Meddelanden](/help/announcements/overview.md) | Få viktiga uppdateringar från Adobe Commerce-teamen. |
| [Felsökning](/help/troubleshooting/overview.md) | Få självbetjäningslösningar och patchar från Adobe Commerce supportteam. |
| [Användarhandbok för Help Center](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Lär dig hur du hanterar supportärenden, ger delad åtkomst och bläddrar effektivt i kunskapsbasen. |
| [Instruktioner](/help/how-to/overview.md) | Få tydliga stegvisa instruktioner från Adobe Commerce supportteam. |
| [Vanliga frågor](/help/faq/overview.md) | Frågor och svar om Adobe Commerce policyer, strategier och information om Adobe Commerce funktioner. |

>[!NOTE]
>
>Om du vill registrera en ny biljett loggar du in på [Adobe Commerce Help Center](https://support.magento.com/) och följer de steg som beskrivs under [Skicka en supportanmälan](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
>
>Om du inte ser alternativet att skicka en biljett läser du avsnittet *[Skicka en biljettlänk som inte visas](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#no-submit-link)* i [användarhandboken för hjälpcentret](/help/help-center-guide/help-center/magento-help-center-user-guide.md).

## Nyheter

<table style="width:100%">
  <tr>
    <th style="width:70%">Beskrivning</th>
    <th style="width:15%">Typ</th>
    <th style="width:15%">Datum</th>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/the-magento-cloud-cli-doesnt-show-an-active-environment">CLI:n <code>Magento-cloud</code> visar ingen aktiv miljö:</a> Det finns flera aktiva miljöer, och du försöker interagera med en miljö genom att köra ett kommandoradskommando för CLI i Magento-molnet. Uppmaningen att välja önskad miljö listar dock inte den här miljön.
    </td>
    <td>Ny artikel</td>
    <td>30 juli 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches">Så här hämtar och använder du en säkerhetspatch:</a> Den här artikeln innehåller instruktioner om hur du hämtar och använder en säkerhetspatch som har släppts, men det finns inga instruktioner.  
    </td>
    <td>Ny artikel</td>
    <td>30 juli 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/falling-back-to-elasticsearch7-when-search-engine-set-to-opensearch">Återgår till Elasticsearch7 när sökmotorn är inställd på OpenSearch:</a> Den här artikeln innehåller en lösning på problemet när ett Falling back to Elasticsearch7-fel inträffar när sökmotorn är inställd på OpenSearch i Adobe Commerce. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-there-are-no-commands-defined-in-the-cache-namespace-error">Distributionen misslyckades: Det finns inga definierade kommandon i namnområdesfelet "cache":</a> Den här artikeln innehåller en lösning på problemet när distributionen misslyckas och ett av de fel som visas i loggen är <em>Det finns inga definierade kommandon i namnområdet "cache"</em>. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-55566-mergecart-mutation-fails-with-an-internal-server-error-in-graphql-response">ACSD-55566: <code>mergeCart</code> mutation misslyckas med internt serverfel i GraphQL-svar:</a> Korrigeringen ACSD-5566 åtgärdar ett problem där <code>mergeCart</code>-mutationen misslyckas med ett internt serverfel i GraphQL-svar. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 har installerats.  
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56546-configurable-and-bundle-products-display-as-out-of-stock-on-the-storefront">ACSD-56546: Konfigurerbara produkter och paketprodukter visas som obefintliga i butiken:</a> Korrigeringsfilen ACSD-56546 åtgärdar ett problem där konfigurerbara produkter och paketprodukter visas som lagrade i butiken. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 har installerats.  
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57565-the-order-dashboard-displays-incorrect-order-information">ACSD-57565: Orderinstrumentpanelen visar felaktig orderinformation:</a> Korrigeringsfilen ACSD-57565 åtgärdar ett problem där orderinstrumentpanelen visar felaktig orderinformation tills tidsperioden uppdateras. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57394-incorrect-product-sorting-by-multiple-sort-fields-in-graphql">ACSD-57394: Felaktig produktsortering efter flera sorteringsattribut i GraphQL:</a> Korrigeringsfilen ACSD-57394 åtgärdar ett problem där produkter sorteras felaktigt när flera sorteringsattribut används i GraphQL. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57854-graphql-response-contains-disabled-categories-that-should-not-be-listed-in-the-category-aggregations">ACSD-57854: GraphQL-svar innehåller inaktiverade kategorier som inte ska listas i kategoriaggregeringar:</a> Korrigeringen ACSD-57854 åtgärdar ett problem där GraphQL-svaret innehåller inaktiverade kategorier som inte ska listas i kategoriaggregeringar. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-57074-yes-no-custom-attribute-does-not-work-with-indexing">ACSD-57074: Anpassat attribut med <code>price_*</code> prefix i <code>attribute_code</code> fungerar inte med indexering:</a> Korrigeringen ACSD-57074 åtgärdar ett problem där det anpassade attributet <em>Yes/No</em> med prefixet <code>price_*</code> i attributet <code>attribute_code</code> inte fungerar med indexering. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-55241-used-and-times-used-attributes-display-incorrect-values-for-generated-coupons">ACSD-55241: Attribut som används och tidsanvändning visar felaktiga värden för genererade kuponger:</a> Korrigeringsfilen ACSD-5241 åtgärdar ett problem där attributen Används och Används visar felaktiga värden för genererade kuponger. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56760-admin-user-is-restricted-to-a-specific-website-and-is-unable-to-sort-or-add-new-products">ACSD-56760: Administratörsanvändaren är begränsad till en viss webbplats och kan inte sortera eller lägga till nya produkter:</a> Korrigeringsfilen ACSD-56760 åtgärdar ett problem där den Admin-användare som är begränsad till en viss webbplats och inte kan sortera eller lägga till nya produkter i en kategori om webbutiken har en egen rotkategori. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56635-imported-customers-are-duplicated-with-the-same-email-address">ACSD-56635: Importerade kunder dupliceras med samma e-postadress när kontodelning är inställd på Global:</a> Korrigeringen ACSD-56635 åtgärdar ett problem där den importerade kunden dupliceras med samma e-postadress när importen används med kontodelning inställd på Global. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57315-new-transaction-created-in-paypal-payflow-pro-each-time-the-fetch-button-is-clicked">ACSD-57315: En ny transaktion skapas i PayPal Payflow Pro varje gång någon klickar på hämtningsknappen:</a> Korrigeringen ACSD-57315 åtgärdar problemet där en ny transaktion skapas i PayPal Payflow Pro varje gång hämtningsknappen klickas på visningstransaktionsskärmen i Admin. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56741-database-setup-upgrade-error-with-custom-mysql-trigger">ACSD-56741: Felsökning av databaskonfigurationsfel med anpassade MySQL-utlösare:</a> Korrigeringen ACSD-56741 åtgärdar ett problem där ett felmeddelande <em>Försöker få åtkomst till matrisförskjutning för värdet av typen null</em> visas under <code>setup:upgrade</code> på grund av en anpassad MySQL-utlösare i databasen som inte är relaterad till indexering och MVViview. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-58008-editing-the-end-date-as-empty-causes-the-schedule-update-to-disappear">ACSD-58008: Om du redigerar slutdatumet som tomt försvinner schemauppdateringen:</a> Korrigeringsfilen ACSD-58008 åtgärdar ett problem där schemauppdateringen försvinner om du redigerar slutdatumet som tomt. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57337-admin-user-with-access-restrictions-can-see-companies">ACSD-57337: Administratörsanvändare med åtkomstbegränsningar kan visa alla företag i företagsrutnätet:</a> Korrigeringsfilen ACSD-57337 åtgärdar ett problem där en administratörsanvändare med åtkomstbegränsningar för specifika webbplatser kan visa företag från alla webbplatser i företagsrutnätet. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-with-correct-access-key-env-composer-auth">Distributionen misslyckas med rätt åtkomstnycklar i <code>env:COMPOSER_AUTH</code> eller <code>auth.json</code>:</a> Den här artikeln tillhandahåller en lösning på problemet när distributionen misslyckas med ett fel som det i distributionsloggen. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-bypass-waf-for-graphql-requests">Så här kringgår du förfrågningar från WAF för GraphQL:</a> I den här artikeln beskrivs hur du kringgår förfrågningar från WAF för GraphQL när Snabbt WAF blockerar dina GraphQL-förfrågningar. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/email-stating-that-export-storage-is-almost-full">E-post som anger att exportlagringsutrymmet är nästan fullt:</a> Den här artikeln innehåller en lösning på problemet där du får ett e-postmeddelande som anger att exportlagringsutrymmet är nästan fullt. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-4-to-10-5-for-magento-commerce-cloud">Uppgradera MariaDB 10.4 till 10.5 för Adobe Commerce i molnet:</a> I den här artikeln beskrivs hur du uppgraderar från MariaDB 10.4 till 10.5 för att fortsätta använda Adobe Commerce i molninfrastrukturen. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/revised-patches-for-google-maps-access-loss-on-all-adobe-commerce-versions">Uppdaterade korrigeringar för åtkomstförlust för Google Maps för alla Adobe Commerce-versioner:</a> Den här artikeln innehåller en korrigering för Adobe Commerce-handlare som inte är kompatibla med några senaste Google Maps-versioner från 3.54+. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102">Säkerhetsuppdatering för Adobe Commerce - APSB24-40:</a> Den här artikeln delar en uppdatering för CVE-2024-34102. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/poor-performance-in-integration-environments">Dåliga prestanda i integreringsmiljöer:</a> Den här artikeln innehåller en lösning på ett problem där Pro-integreringsmiljöerna och startmiljöer fungerar dåligt. 
    </td>
    <td>Ny artikel </td>
    <td>30 juli 2024</td>
 </tr>
</table>

## Populära artiklar

* [Byt till OpenSearch för Adobe Commerce i molnet 2.4.4](/help/announcements/adobe-commerce-announcements/switching-to-opensearch-for-adobe-commerce-on-cloud-2-4-4.md)
* [Apache log4j2-sårbarhet i Adobe Commerce](/help/announcements/adobe-commerce-announcements/apache-log4j2-adobe-commerce.md)
* [Säkerhetsuppdateringar för Adobe Commerce APSB22-12](/help/troubleshooting/known-issues-patches-attached/0-day-vulnerability-patch.md)
* [Identifiera och mäta avbrott för Adobe Commerce i molninfrastrukturen](/help/how-to/general/how-to-identify-outages.md)
* [Visa miljöns vCPU-nivå i ditt kluster på Adobe Commerce](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)
* [Adobe Commerce i molninfrastruktur: Beräkning av processorallokering](/help/how-to/general/magento-commerce-cloud-cpu-allocation-calculation.md)
* [Adobe Commerce i molninfrastruktur: Kontrollera värddatorns CPU-konfiguration](/help/how-to/general/magento-commerce-cloud-check-hosts-cpu-configuration.md)
