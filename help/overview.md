---
title: Adobe Commerce Support Knowledge Base
description: Allt du behöver veta för att felsöka och underhålla din Commerce Store.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 95509b717d41436b68ad94c3c28ac72e1887fdfc
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 1%

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
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-update-the-cloud-account-profile">Så här uppdaterar du molnkontoprofilen:</a> I den här artikeln beskrivs hur du ändrar profilen på molnkontot.
    </td>
    <td>Ny artikel</td>
    <td>22 april 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/admin-create-order-page-in-csp-restricted-mode">Felsök Skapa beställningssida i begränsat CSP-läge:</a> I den här artikeln finns förklaringar och korrigeringar för Adobe Commerce 2.4.7-problem när du skapar en order på administratörssidan när begränsat CSP-läge är <em>aktiverat</em>.  
    </td>
    <td>Ny artikel</td>
    <td>22 april 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/storefront-checkout-page-in-csp-restricted-mode">Felsök utcheckningssidan för butiker i begränsat läge för CSP:</a> Den här artikeln innehåller förklaringar och korrigeringar för Adobe Commerce 2.4.7-problem när du visar utcheckningssidan i begränsat läge för CSP, med felmeddelandet <em>"Avvisat att köra infogat skript eftersom det bryter mot följande direktiv för innehållets säkerhetsprincip: "script-src ..."</em> i webbläsarkonsolloggen. 
    </td>
    <td>Ny artikel </td>
    <td>22 april 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-54656-invisible-recaptcha-fails-during-checkout-preventing-order-placement">ACSD-54656: Osynlig reCAPTCHA fungerar inte under utcheckning och förhindrar därför att beställningen placeras:</a> Korrigeringsfilen ACSD-54656 åtgärdar ett fel där osynlig reCAPTCHA inte fungerar korrekt under utcheckning, vilket förhindrar att en beställning placeras. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.46 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>22 april 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-46767-category-page-caches-invalidate-when-the-stock-quantity-changes">ACSD-46767: Kategorisidans cachning blir ogiltig när lagerkvantiteten ändras:</a> Korrigeringsfilen ACSD-46767 åtgärdar ett problem där kategorisidan cachar blir ogiltig när lagerkvantiteten ändras, även om produkten fortfarande finns i lager. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.46 har installerats.  
    </td>
    <td>Ny artikel </td>
    <td>22 april 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-45/acsd-56415-performance-of-partial-price-indexing-is-slowed-down-due-to-a-delete-query">ACSD-56415: Prestanda för partiell prisindexering har blivit långsammare på grund av DELETE-fråga:</a> Korrigeringen ACSD-56415 åtgärdar ett problem där prestandan för partiell prisindexering har blivit långsammare på grund av en DELETE-fråga när databasen har många partiella prisdataindex. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.45 har installerats.  
    </td>
    <td>Ny artikel </td>
    <td>22 april 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56858-role-permissions-display-issue-in-b2b-company-admin-panel">ACSD-56858: Skillnad i rollbehörigheter i B2B-företagsadministratör:</a> Korrigeringen för ACSD-56858 åtgärdar ett problem där rollbehörigheter felaktigt visas för en företagsadministratör med begränsat ansvar i B2B-miljön. Den här korrigeringen är tillgänglig när <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 har installerats. 
    </td>
    <td>Ny artikel </td>
    <td>22 april 2024</td>
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
