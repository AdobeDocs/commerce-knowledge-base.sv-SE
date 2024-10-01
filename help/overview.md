---
title: Adobe Commerce Support Knowledge Base
description: Allt du behöver veta för att felsöka och underhålla din Commerce Store.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 24c7783ca6d25f8cb13e7fe84efdb6cf09efcfa6
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 1%

---

# Adobe Commerce Support Knowledge Base

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
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/data-connection-customer-profiles-not-exported">Kundprofiler visas inte i Experience Platform:</a> I den här artikeln beskrivs felsökningssteg om kundprofildata inte visas i Experience Platform när du använder dataanslutningstillägget.
    </td>
    <td>Ny artikel</td>
    <td>27 augusti 2024</td>
  </tr>

<tr>  
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-dashboard-ranking-incorrect">Kontrollpanelen för Live-sökning och rankningen av sökresultat är felaktig:</a> I den här artikeln förklaras varför de data som visas på kontrollpanelen för Live-sökning kan vara felaktiga eller varför rankningen av sökresultaten kanske inte är som du förväntade dig.  
    </td>
    <td>Ny artikel</td>
    <td>27 augusti 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102">Felsöka rotering av krypteringsnyckel: CVE-2024-34102:</a> Den här artikeln är avsedd att hjälpa handlare att felsöka rotering av krypteringsnyckel efter att de redan har följt stegen som beskrivs i den här <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102">artikeln</a> på CVE-2024-34102. 
    </td>
    <td>Ny artikel </td>
    <td>27 augusti 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/news/decommissioning-of-adobe-commerce-help-center">Avställning av Adobe Commerce Help Center:</a> Under vår resa har Adobe Commerce migrerat vår process för supportinhämtning från Adobe Commerce Help Center till Adobe Experience League för att vara bättre ansluten till Adobe. 
    </td>
    <td>Ny artikel </td>
    <td>27 augusti 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61">Säkerhetsuppdatering för Adobe Commerce - APSB24-61:</a> Uppdateringen åtgärdar allvarliga, viktiga och måttliga säkerhetsluckor Ett lyckat utnyttjande kan leda till godtycklig kodkörning, läsning av godtyckliga filsystem, åsidosättande av säkerhetsfunktioner och eskalering av behörigheter. Bulletinen är Adobe Security Bulletin (APSB24-61). 
    </td>
    <td>Ny artikel </td>
    <td>27 augusti 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-facets-not-sorted">Live Search-ansikten är inte sorterade i bokstavsordning:</a> I den här artikeln förklaras problemet med att alla Adobe Commerce storefront-aspekter sorteras i bokstavsordning med alternativ för en enstaka markering, oavsett vilken indatatyp som tilldelats motsvarande attribut. 
    </td>
    <td>Ny artikel </td>
    <td>27 augusti 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/guidance-on-securing-your-store-and-rotating-encryptionkeys-cve-2024-34102">Vägledning om hur du skyddar din butik och roterar krypteringsnycklar: CVE-2024-34102:</a> I den här artikeln finns vägledning om hur du skyddar din butik och roterar krypteringsnycklar. 
    </td>
    <td>Ny artikel </td>
    <td>27 augusti 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mdee-table-does-not-exist">Det finns inga korrigeringsdata som inte har uppdaterats i Commerce Data Exporter-feeds och kron loggar fel med ändringsloggtabellen:</a> Den här artikeln innehåller en lösning för att åtgärda datasynkroniseringsproblem som orsakas av att fel visnings-ID används i prenumerationen för Data Exporter Mview. Mview-prenumerationen används för att spåra ändringar i databastabeller. 
    </td>
    <td>Ny artikel </td>
    <td>27 augusti 2024</td>
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
