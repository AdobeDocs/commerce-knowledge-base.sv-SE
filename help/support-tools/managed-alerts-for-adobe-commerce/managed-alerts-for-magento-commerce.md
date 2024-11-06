---
title: Hanterade aviseringar för Adobe Commerce
description: Om du använder en Adobe Commerce-plan på Cloud Infrastructure Pro-planarkitekturen kan du använda hanterade aviseringar för att förstå webbplatsens hälsa. Om du är kund hos Adobe Commerce om arkitekturarkitektur för molninfrastruktur får du bara varningar om villkoren för Apdex och felfrekvens.
exl-id: 4d08eaad-a3ce-4f6c-9c32-58e44e1d6534
feature: Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Hanterade aviseringar för Adobe Commerce


Vi har konfigurerat viktiga instrumentpaneler och varningar som hjälper dig att förstå när din webbplats når kritisk lagring och Apdex-nivåer (användarnas tillfredsställelse med svarstid för program och tjänster). Detta kan hjälpa dig att vidta åtgärder innan du märker att svarstiderna tar lång tid eller att ett driftstopp inträffar. Du kan felsöka varningarna med artiklarna nedan. Innan du kan använda varningarna måste du först konfigurera meddelandekanaler. Se [New Relic Konfigurera meddelandekanaler](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service) i utvecklardokumentationen.

>[!NOTE]
>
>Om det inte finns några hanterade aviseringar för Adobe Commerce-aviseringsprincipen kan det bero på att det här kontot har skapats nyligen eller att New Relic har konfigurerats nyligen. En process körs varje tisdag för att lägga till varningsprincipen till dessa konton. Varningspolicyn bör vara tillgänglig dagen efter att nästa process har körts. Om principen fortfarande saknas [skickar du en supportförfrågan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) från Adobe Commerce och inkluderar ditt projekt-ID.

I tabellen nedan finns länkar till KB-artiklar med felsökningssteg för dessa aviseringar:

* Hanterade varningar för Adobe Commerce: CPU-varning
* Hanterade varningar för Adobe Commerce: CPU-kritisk varning
* Hanterade varningar för Adobe Commerce: minnesvarning
* Hanterade varningar för Adobe Commerce: minneskritisk varning
* Hanterade aviseringar för Adobe Commerce: Adexvarning
* Hanterade aviseringar för Adobe Commerce: ADOBE-varning
* Hanterade varningar för Adobe Commerce: diskvarning
* Hanterade varningar för Adobe Commerce: Diskkritisk varning
* Hanterade aviseringar om Adobe Commerce: MariaDB-aviseringar
* Hanterade varningar på Adobe Commerce: Redis Memory Warning
* Hanterade varningar på Adobe Commerce: Redis-minneskritisk varning

>[!NOTE]
>
>De fastställda tröskelvärdena för både varningsmeddelanden och kritiska aviseringar baseras på forskning vi gör med hjälp av historiska resultatdata för hela vår kundbas, och representerar de senaste insikterna från Adobe Commerce support- och konstruktionsgrupper. Observera att dessa tröskelvärden kan ändras baserat på den senaste, pågående analysen. Det typiska varningsflödet är att få varningar som är mindre eller större vad gäller allvarlighetsgrad. Du kommer förmodligen få en varning innan du får en viktig varning. Mer information om felsökningsåtgärder finns i länkarna till artiklar.

<table style="width: 128.434%; height: 660px;" width="100%">
<tbody>
<tr style="height: 44px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 44px;">
<p><strong>Allvarlighetsgrad</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 44px;">
<p><strong>CPU</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 44px;">
<p><strong>Minne</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 44px;">
<p><strong>Skiva</strong></p>
</td>
<td class='"wysiwyg-text-align-center wysiwyg-text-align-center' style="width: 9%; height: 44px;">
<p><strong>Apdex</strong></p>
</td>
<td style="width: 7.058036%; height: 44px;">
<p><strong>MariaDB</strong></p>
</td>
<td class="wysiwyg-text-align-center med-col">
<p><strong>Redis-minne</strong></p>
</td>
<td class="wysiwyg-text-align-center large-col" style="width: 24.5638%; height: 44px;">
<p><strong>Felsökning av artikel</strong></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Varning</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-cpu-warning-alert.md">Hanterade varningar för Adobe Commerce: CPU-varning</a><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-cpu-warning-alert.md"></a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Kritisk</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-cpu-critical-alert.md">Hanterade varningar för Adobe Commerce: CPU-kritisk varning</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Varning</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-memory-warning-alert.md">Hanterade varningar för Adobe Commerce: minnesvarning</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Kritisk</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;">
<p> </p>
<p>✅</p>
</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-memory-critical-alert.md#_critical_memory">Hanterade varningar för Adobe Commerce: minneskritisk varning</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Varning</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;">✅</td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Hanterade aviseringar för Adobe Commerce: Adexvarning</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Kritisk</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;">✅</td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-critical-alert.md">Hanterade aviseringar för Adobe Commerce: ADOBE-varning</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Varning</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert.md" title="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert.md">Hanterade varningar för Adobe Commerce: diskvarning</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Kritisk</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert.md" title="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert.md">Hanterade varningar för Adobe Commerce: Diskkritisk varning</a></p>
</td>
</tr>
<tr style="height: 44px;">
<td style="width: 17.8571%; height: 44px;">Varning och kritisk</td>
<td style="width: 6.14286%; height: 44px;"> </td>
<td style="width: 10.5714%; height: 44px;"> </td>
<td style="width: 7.14286%; height: 44px;"> </td>
<td style="width: 9%; height: 44px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 44px;">✅</td>
<td style="width: 24.5638%; height: 44px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 44px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-mariadb-alerts.md">Hanterade aviseringar om Adobe Commerce: MariaDB-aviseringar</a></p>
</td>
</tr>
<tr style="height: 22px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 22px;">Varning</td>
<td style="width: 6.14286%; height: 22px;"> </td>
<td style="width: 10.5714%; height: 22px;"> </td>
<td style="width: 7.14286%; height: 22px;"> </td>
<td style="width: 9%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 24.5638%; height: 22px;">
<p>✅</p>
</td>
<td style="width: 24.5638%; height: 22px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-redis-memory-warning-alert.md">Hanterade varningar på Adobe Commerce: Redis Memory Warning</a></p>
</td>
</tr>
<tr style="height: 22px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 22px;">Kritisk</td>
<td style="width: 6.14286%; height: 22px;"> </td>
<td style="width: 10.5714%; height: 22px;"> </td>
<td style="width: 7.14286%; height: 22px;"> </td>
<td style="width: 9%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 24.5638%; height: 22px;">
<p>✅</p>
</td>
<td style="width: 24.5638%; height: 22px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-redis-memory-critical-alert.md">Hanterade varningar på Adobe Commerce: Redis-minneskritisk varning</a></p>
</td>
</tr>
</tbody>
</table>
