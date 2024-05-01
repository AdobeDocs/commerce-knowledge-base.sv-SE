---
title: Felsökning för avancerad rapportering för Adobe Commerce
description: Du kan lösa problem med avancerad rapportering på Adobe Commerce med hjälp av det här felsökningsverktyget. Detta inkluderar avancerad rapportering som inte visar några data och 404 fel. Klicka på varje fråga för att visa svaret i varje steg i felsökaren.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 84b4ca4c4144381f0b404d2eae6684e7b21755df
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Felsökning för avancerad rapportering för Adobe Commerce

Du kan lösa problem med avancerad rapportering på Adobe Commerce med hjälp av det här felsökningsverktyget. Detta inkluderar avancerad rapportering som inte visar några data och 404 fel. Klicka på varje fråga för att visa svaret i varje steg i felsökaren.

## Steg 1 - Bekräfta att webbplatsen uppfyller avancerade rapporteringskrav {#step-1}

+++**Uppfyller webbplatsen kraven på avancerad rapportering?**

Du har en 404-felsida när du använder Avancerad rapportering. Möter din webbplats [Avancerade rapporteringskrav](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements)?

a. JA - Fortsätt till [Steg 2](#step-2).\
b. NEJ - Slutför de avancerade rapporteringskraven för din webbplats genom att följa stegen i [Avancerade rapporteringskrav](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements). Fortsätt sedan till [Steg 2](#step-2).

+++

## Steg 2 - Finns det order i flera basvalutor? {#step-2}

+++**Används flera basvalutor?**

Används flera basvalutor (i order och konfiguration)? Kör det här SQL-kommandot för att hämta den aktuella konfigurationen: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. JA - Om frågan returnerar flera rader kan du inte använda Avancerad rapportering eftersom vi bara har stöd för en valuta.\
b. NEJ - Utdata visar endast en valuta. Exempel: `USD`. Har flera basvalutor använts (i order)? Kör det här SQL-kommandot för att hämta historikorderdata:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**Obs! Det här kommandot kräver en fullständig tabellsökning, så för tabeller med ett stort antal poster kan detta påverka prestanda medan frågan körs.** för att få historiska orderdata.
Om flera basvalutor har använts kan du inte använda avancerad rapportering eftersom vi bara har stöd för en valuta. Om utdata endast visar en valuta går du vidare till [Steg 3](#step-3).

+++

## Steg 3 - Kontrollera om en delad databas används {#step-3}

+++**Använder du en delad databaslösning?**

Använder du [delad databaslösning](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html)?

a. JA - Använd plåstret **MDVA-26831** in [Advanced Reporting 404 error on split database solution](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-404-error-on-split-database-solution.md) och rensa cache. Vänta i 24 timmar tills jobbet körs igen och försök igen.\
b. NEJ - Fortsätt till [Steg 4](#step-4).

+++

## Steg 4 - Bekräfta avancerad rapportering aktiverat {#step-4}

+++**Är avancerad rapportering aktiverat?**

Kontrollera **Administratör** > **Lager** > **Inställningar** > **Konfiguration** > **Allmänt** > **Avancerat**. Detaljerade anvisningar finns i [Avancerad rapportering: Aktivera avancerad rapportering](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting).

a. JA - Fortsätt till [Steg 5](#step-5).\
b. NEJ - [Aktivera avancerad rapportering](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) och spara och vänta i 24 timmar på att Adobe Commerce och Advanced Reporting ska synkroniseras. Kontrollera om dina data nu läses in. Om den gör det har du löst problemet. Om det inte går vidare till [Steg 5](#step-5).

+++

## Steg 5 - Sök efter token {#step-5}

+++**Finns det en token?**

Kontrollera att det finns en token genom att köra följande fråga: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` Finns det en token?

a. JA - Fortsätt till [Steg 7](#step-7).\
b. NO - Om tokenvärdet är NULL eller om det inte finns någon post i databasen fortsätter du till [Steg 6](#step-6).

+++

## Steg 6 - Använd raden {#step-6}

+++**Returnerar frågan raden?**

Kontrollera räknarvärdet i flaggtabellen genom att köra den här frågan: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` Returnerar frågan raden?

a. JA - Gör följande: 1. Kör frågan nedan:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [Inaktivera och aktivera modulen Avancerad rapportering](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) i inställningar och [auktorisera om token](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
3\. Vänta i 24 timmar tills Adobe Commerce och Advanced Reporting har synkroniserats. Om du fortfarande inte kan se data i avancerad rapportering, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Om frågan inte returnerar något, gör du så här: 1. [Inaktivera och aktivera modulen Avancerad rapportering](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) i inställningar och [auktorisera om token](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
2\. Vänta i 24 timmar tills Adobe Commerce och Advanced Reporting har synkroniserats. Om du fortfarande inte kan se data i avancerad rapportering, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 7 - Sök efter poster i `cron_schedule` table {#step-7}

+++**Finns det poster i `cron_schedule` bord?**

Kontrollera jobbet `analytics_collect_data` kördes genom att köra den här frågan: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. JA - Om det finns poster och **status** kolumn säger _missad_ använder du patchen i den här KB-artikeln [Uppdatera avancerad rapportering för att köras på en egen kreditgrupp](/help/troubleshooting/known-issues-patches-attached/update-advanced-reporting-to-run-on-its-own-cron-group.md).\
b. JA - Om det finns poster och **status** kolumn säger _framgång_, fortsätta till [Steg 9](#step-9).\
c. YES - If there are records and the **status** kolumn säger _fel_, fortsätta till [Steg 8.](#step-8)\
d. NO - Om det inte finns några poster, fortsätt till [Steg 8](#step-8).

+++

## Steg 8 - Sök efter jobb i `support_report.log` {#step-8}

+++**Var jobbet inloggat `support_report.log`?**

Kör kommandot: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. JA - Om utdata från frågan indikerar ett slutfört jobb, till exempel `Cron Job analytics_collect_data is successfully finished` fortsätta till [Steg 9](#step-9).\
b. NO - Om det inte finns några poster i loggen, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. JA - Om det finns poster, men det finns ett fel, fortsätter du till [Steg 10](#step-10).

+++

## Steg 9 - sök efter `data.tgz` fil {#step-9}

+++**Gör filen `data.tgz` finns i systemet och finns det poster i åtkomstloggarna?**

Kontrollera att filen `data.tgz` exists, run command:

```
ls -ltr pub/media/analytics/<there should be a directory with hash name>/
```

Kör kommando för att kontrollera att det finns poster i access.logs:

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a. JA - Om filen `data.tgz` finns och det finns poster i åtkomstloggarna, men du har fortfarande ett 404-fel. Du måste [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEJ - Fortsätt till [Steg 10](#step-10).

+++

## Steg 10 - Kontrollera felmeddelandet {#step-10}

+++**Är det ett felmeddelande som genereras av cron-jobbet?**

Exempel: I `core_config_data` tabellen där du ser felet *Filen &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0 kan inte tas bort*. Varning!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0?lang=en): Ingen sådan fil eller katalog*

a. JA - Använd plåstret ACSD-50165 i [Det går inte att ta bort filen. Varning!unlink: Det finns inget sådant fil- eller katalogfel från administratören](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md), vänta i 24 timmar tills jobbet körs igen och försök sedan igen.\
b. NEJ - Fortsätt till [Steg 11](#step-11).

+++

## Steg 11 - Kontrollera om det finns ett Page Builder-fel {#step-11}

+++**Är det något fel som orsakas av Page Builder?**

Exempel: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. JA - Använd MDVA-19391-plåstret i [Vanliga fel i serierapporteringen på Adobe Commerce](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-cron-job-errors-magento-commerce.md), vänta 24 timmar tills jobbet körs igen och försök igen.\
b. NEJ - [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Tillbaka till steg 1](#step-1)
