---
title: Diagnostisera en datadiskrepans
description: Den här artikeln innehåller lösningar för felsökning av avvikelser mellan en Magento Business Intelligence-rapport (MBI) och en frågerapport eller en tredjepartsrapport.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Diagnostisera en datadiskrepans

Den här artikeln innehåller lösningar för felsökning av avvikelser mellan en Magento Business Intelligence-rapport (MBI) och en frågerapport eller en tredjepartsrapport.

Beroende på hur komplex din analys är kan det krävas att du känner till ett antal olika aspekter av plattformen för att kunna generera motsvarande MBI-rapport. Den här checklistan och de relaterade länkarna hjälper dig att förstå logiken bakom rapporten, så att du kan identifiera orsaken till eventuella avvikelser.

1. Om någon annan i teamet skapade rapporten börjar du med att bekräfta målet och parametrarna för analysen.
1. Generera förväntade datapunkter att jämföra med MBI-rapporten baserat på en fråga, ett rapportverktyg från tredje part eller en formel.
1. Granska och bekräfta [metrisk](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html?lang=sv-SE)-definitioner, antingen från måttlänken i Report Builder eller genom att gå till fliken [Systemsammanfattning](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary):
   * Datatabell
   * Åtgärd
   * Operandkolumn, inklusive dess beräkning om den har härletts (via Systemsammanfattning)
   * Tidsstämpel
   * För prenumerationsvärden: start- och slutdatum
   * Filter, inklusive de som finns i [filteruppsättningar](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html?lang=sv-SE) tillämpade
1. Granska och bekräfta annan datahantering i rapporten:
   * Beräknade formler
   * [Grupperingar](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=sv-SE#groupby)
   * [Perspektiv](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=sv-SE)
   * [Tidsalternativ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=sv-SE)
   * För [kohortanalys](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Kohortdatum
   * För [kohortanalys](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Kohortperspektiv
1. Om diskrepansen innehåller aktuella data bekräftar du den senaste tillgängliga datapunkten genom att gå till avsnittet **Uppdateringsinformation** på sidan Anslutningar.
1. Om ett mätvärde som används i analysen bygger på en tabell från din databas där rader någonsin tas bort från den tabellen, bekräftar du med MBI Support Team att tabellen kontrolleras för borttagna rader samt hur ofta kontrollen och [replikeringsmetoden](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html?lang=sv-SE) görs för tabellen.
1. Om kolumner som används i analysen kan ändras efter att en rad har lagts till bekräftar du med stöd för att de här kolumnerna [kontrolleras för ändringar](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html?lang=sv-SE), liksom frekvensen för omkontrollen.

**Fortfarande stumpad?** Oroa dig inte - vi är här för att hjälpa till. Skicka oss en begäran med [dessa instruktioner](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).

## Relaterad läsning

[Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
