---
title: Felsökning för avancerad rapportering för Adobe Commerce
description: Du kan lösa problem med avancerad rapportering på Adobe Commerce med hjälp av det här felsökningsverktyget. Detta inkluderar avancerad rapportering som inte visar några data och 404 fel. Klicka på varje fråga för att visa svaret i varje steg i felsökaren.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 207fd4cd11f76a5076e98cda8b6776b2d68ef937
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 0%

---

# Felsökning för avancerad rapportering för Adobe Commerce

Du kan lösa problem med avancerad rapportering på Adobe Commerce med hjälp av det här felsökningsverktyget. Detta inkluderar avancerad rapportering som inte visar några data och 404 fel. Klicka på varje fråga för att visa svaret i varje steg i felsökaren.

## Steg 1 - Bekräfta att webbplatsen uppfyller avancerade rapporteringskrav {#step-1}

+++**Uppfyller din webbplats avancerade rapporteringskrav?**

Du har en 404-felsida när du använder Avancerad rapportering. Uppfyller webbplatsen [avancerade rapporteringskrav](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)?

a. JA - Fortsätt till [Steg 2](#step-2).\
b. NEJ - Slutför de avancerade rapporteringskraven för din webbplats genom att följa stegen i [Avancerade rapporteringskrav](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements). Fortsätt sedan till [Steg 2](#step-2).

+++

## Steg 2 - Finns det order i flera basvalutor? {#step-2}

+++**Används flera basvalutor?**

Används flera basvalutor (i order och konfiguration)? Kör det här [!DNL SQL]-kommandot för att hämta den aktuella konfigurationen: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';`.

a. JA - Om frågan returnerar flera rader kan du inte använda Avancerad rapportering eftersom vi bara har stöd för en valuta.\
b. NEJ - Utdata visar endast en valuta. Exempel: `USD`. Har flera basvalutor använts (i order)? Kör det här [!DNL SQL]-kommandot för att hämta historikorderdata:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**Obs! Det här kommandot kräver en fullständig tabellsökning, så för tabeller med ett stort antal poster kan detta påverka prestanda medan frågan kör** för att hämta historiska orderdata.
Om flera basvalutor har använts kan du inte använda avancerad rapportering eftersom vi bara har stöd för en valuta. Om utdata endast visar en valuta fortsätter du till [steg 3](#step-3).

+++

## Steg 3 - Kontrollera om en delad databas används {#step-3}

+++**Använder du en delad databaslösning?**

Använder du [delad databaslösning](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)?

a. JA - Använd korrigeringen **MDVA-26831** i Advanced Reporting 404-felet för delad databaslösning och rensning av cache. Vänta i 24 timmar tills jobbet körs igen och försök igen.\
b. NEJ - Fortsätt till [steg 4](#step-4).

+++

## Steg 4 - Bekräfta avancerad rapportering aktiverat {#step-4}

+++**Är avancerad rapportering aktiverat?**

Kontrollera **Admin** > **Lagrar** > **Inställningar** > **Konfiguration** > **Allmänt** > **Avancerad rapportering**. Granska [Avancerad rapportering: Aktivera avancerad rapportering](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) om du vill ha mer information.

a. JA - Fortsätt till [steg 5](#step-5).\
b. NEJ - [Aktivera avancerad rapportering](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) och spara, och vänta i 24 timmar på att Adobe Commerce och Advanced Reporting ska synkroniseras. Kontrollera om dina data nu läses in. Om den gör det har du löst problemet. Om det inte fortsätter till [steg 5](#step-5).

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
2\. [Inaktivera och aktivera modulen för avancerad rapportering](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) i inställningarna och [auktorisera token igen](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
3\. Vänta i 24 timmar tills Adobe Commerce och Advanced Reporting har synkroniserats. Om du fortfarande inte kan se data i avancerad rapportering [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Om frågan inte returnerar något, gör du så här: 1. [Inaktivera och aktivera modulen för avancerad rapportering](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) i inställningarna och [auktorisera token igen](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
2\. Vänta i 24 timmar tills Adobe Commerce och Advanced Reporting har synkroniserats. Om du fortfarande inte kan se data i avancerad rapportering [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 7 - Sök efter poster i tabellen `cron_schedule` {#step-7}

+++**Finns det poster i tabellen `cron_schedule`?**

Kontrollera att jobbet `analytics_collect_data` kördes genom att köra frågan: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. JA - Om det finns poster och kolumnen **status** säger _missade_ använder du korrigeringen i den här KB-artikeln Uppdatera avancerad rapportering för att köra den på en egen cron-grupp.\
b. JA - Om det finns poster och kolumnen **status** säger _success_ fortsätter du till [steg 9](#step-9).\
c. JA - Om det finns poster och kolumnen **status** säger _error_ fortsätter du till [steg 8.](#step-8)\
d. NEJ - Om det inte finns några poster fortsätter du till [steg 8](#step-8).

+++

## Steg 8 - Sök efter jobb i `support_report.log` {#step-8}

+++**Var jobbet inloggat `support_report.log`?**

Kör kommandot: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. JA - Om utdata från frågan indikerar ett slutfört jobb, till exempel `Cron Job analytics_collect_data is successfully finished`, fortsätter du till [Steg 9](#step-9).\
b. NEJ - Om det inte finns några poster i loggen [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. JA - Om det finns poster men ett fel uppstår går du vidare till [Steg 10](#step-10).

+++

## Steg 9 - Sök efter filen `data.tgz` {#step-9}

+++**Finns filen `data.tgz` i systemet och finns det poster i åtkomstloggarna?**

Om du vill kontrollera att filen `data.tgz` finns kör du det här kommandot - det bör returnera katalog(er) med hash-namn:

```
ls -ltr pub/media/analytics/
```

Kör det här kommandot om du vill kontrollera att det finns poster i access.logs:

* På Commerce Cloud:

  ```
  {{zgrep -i analytics /var/log/platform/*/access.log* | grep MagentoBI}}
  ```

* Vid Lokal ersätter du filsökvägen i enlighet med detta:
  `zgrep -i analytics <your web server's log path>/access.log* | grep MagentoBI`

a. JA - Om filen `data.tgz` finns med och det finns poster i åtkomstloggarna, men du fortfarande har ett 404-fel, måste du [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEJ - Fortsätt till [steg 10](#step-10).

+++

## Steg 10 - Kontrollera felmeddelandet {#step-10}

+++**Har kron-jobbet gett upphov till ett felmeddelande?**

Exempel: I tabellen `cron_schedule` ser du felet *Filen &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0 kan inte tas bort*. Varning!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0?lang=en): Ingen sådan fil eller katalog*

a. JA - Använd ACSD-50165-korrigeringen i [Det går inte att ta bort filen. Varning!unlink: Det finns inget sådant fil- eller katalogfel från Admin](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md), vänta 24 timmar tills jobbet körs igen och försök sedan igen.\
b. NEJ - Fortsätt till [steg 11](#step-11).

+++

## Steg 11 - Kontrollera om det finns ett Page Builder-fel {#step-11}

+++**Har Page Builder orsakat ett fel?**

Exempel: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. JA - Använd MDVA-19391-korrigeringen i Common Advanced Reporting cron-jobbfel på Adobe Commerce, vänta 24 timmar tills jobbet körs igen och försök igen.\
b. NEJ - [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Tillbaka till steg 1](#step-1)

## Relaterad läsning

[Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
