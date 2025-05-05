---
title: Felsökning av Adobe Commerce webbplats ned
description: Klicka på varje fråga för att visa svarsinformationen i varje steg i felsökaren.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---

# Felsökning av Adobe Commerce webbplats ned

Klicka på varje fråga för att visa svarsinformationen i varje steg i felsökaren.

## Steg 1 {#step-1}

+++**Visar <https://status.adobe.com> några problem?**

a. JA - Om du har markerat [Adobe Commerce-status](https://status.adobe.com/cloud/experience_cloud) och ett problem har uppstått öppnar du en [supportbiljett](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) för ytterligare information.\
b. NEJ - Om du har markerat [Adobe Commerce-status](https://status.adobe.com/cloud/experience_cloud) och det inte har uppstått något problem går du vidare till [Steg 2](#step-2).

+++

## Steg 2 {#step-2}

+++**Visar http://status.fastly.com några problem?**

a. JA - Om du har markerat [[!DNL Fastly] Status](https://status.fastly.com/) och det har uppstått ett problem, öppnar du en [supportbiljett](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) för ytterligare information.\
b. NEJ - Om du har markerat [[!DNL Fastly] Status](https://status.fastly.com/) och det inte gick att visa ett problem går du vidare till [Steg 3](#step-3).

+++

## Steg 3 {#step-3}

+++**Kontrollera webbplatsen i en webbläsare. Får du en 200-kod (OK)?**

Så här kontrollerar du felkoder i **Firefox**: Klicka på ikonen **Öppna meny** > **Webbutvecklare** > **Växla verktyg** > fliken **Nätverk** > **Alla** filter > kolumnen **Status** . Så här kontrollerar du felkoder i **Chrome**: Klicka på ikonen **Öppna meny** > **Fler verktyg** > **Utvecklarverktyg** > fliken **Nätverk** > **Alla** filter > kolumnen **Status** .

a. JA - Öppna en [supportbiljett](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) om du vill ha mer information.\
b. NEJ - Fortsätt till [steg 4](#step-4).

+++

## Steg 4 {#step-4}

+++**Vilken webbplatsfelkod fick du?**

a. Felkod 500 - Kontrollera loggen för `/var/log/platform/`. Om dessa data inte utgör problemet för dig kan du öppna en [supportanmälan](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) och inkludera den felsökningsinformation som du har gjort hittills för ytterligare utredning.

b. Felkod 503 - Kontrollera loggen för `var/reports`. Om dessa data inte utgör problemet för dig kan du öppna en [supportanmälan](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) och inkludera den felsökningsinformation som du har gjort hittills för ytterligare utredning.

c. Felkod 404 - Kör följande fråga: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Om frågan returnerar en tabell där `update_exists`-värdet är &quot;0&quot;, se artikeln [Error 404 på alla sidor, butiker och administratörer på grund av problem med innehållsmellanlagring](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue) . I alla andra fall fortsätter du till [steg 5](#step-5).

d. Andra felkoder - fortsätt till [steg 5](#step-5).

+++

## Steg 5 {#step-5}

+++**Är platsen långsam, eller har hög serverbelastning, hög processorbelastning, långsam behandling av begäranden eller avbrott i [!DNL MySQL] eller Redis?**

a. JA - Fortsätt med steg för [Sökning efter DDOS-attacker från CLI](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli).\
b. NO - Kontrollera loggarna för `/var/log/exception.log` och `/var/log/deploy.log`, och om dessa data inte utgör problemet för dig, gå till [steg 6](#step-6).

+++

## Steg 6 {#step-6}

+++**Har du distributionsfel eller distributionsfel?**

a. JA - Fortsätt till [steg 13](#step-13).\
b. NEJ - Fortsätt till [steg 7](#step-7).

+++

## Steg 7 {#step-7}

+++**Har du fel i Elasticsearch?**

a. JA - Fortsätt med steg för att [kontrollera Elasticsearch](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/search/configure-search-engine).
b. NEJ - Fortsätt till [steg 8](#step-8).

+++

## Steg 8 {#step-8}

+++**Har din [!DNL MySQL]-databas långsamma frågor eller felaktiga frågor?**

a. JA - Fortsätt med [Kontrollera långsamma frågor och processer som tar för lång tid i [!DNL MySQL]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql) and checking your query structure in this [[!DNL MySQL] frågesjälvstudiekursen](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NEJ - Fortsätt till [steg 9](#step-9).

+++

## Steg 9 {#step-9}

+++**Är ditt statiska innehåll inte tillgängligt?**

a. JA - fortsätt med att konsultera artikeln [Kontrollera statiskt innehåll](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment).\
b. NEJ - Fortsätt till [steg 10](#step-10).

+++

## Steg 10 {#step-10}

+++**Ser du allvarliga PHP-fel i dina loggar?**

a. JA - fortsätt med att konsultera [vanliga PHP-allvarliga fel och lösningar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions).\
b. NEJ - Fortsätt till [steg 11](#step-11).

+++

## Steg 11 {#step-11}

+++**Ser du Redis-fel?**

a. JA - Fortsätt med stegen för att [verifiera [!DNL Redis] körs](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection) och för [[!DNL Redis] felsökning](https://redis.io/topics/problems).\
b. NEJ - Fortsätt till [steg 12](#step-12).

+++

## Steg 12 {#step-12}

+++**Ser du indexeringsfel?**

a. JA - Om indexet är låst av en annan process läser du [Index är låst av en annan process](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/index-is-locked-by-another-process). Om du har andra indexeringsfel öppnar du en [supportbiljett](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) för ytterligare information.\
b. NEJ - Öppna en [supportbiljett](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) om du vill ha mer information.

+++

## Steg 13 {#step-13}

+++**Har du problem med dina anpassade moduler?**

a. JA - Gå till [Allmän felsökningshjälp för anpassad modul](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help).\
b. NEJ - Fortsätt till [steg 14](#step-14).

+++

## Steg 14 {#step-14}

+++**Har du fel efter krok?**

a. JA - Fortsätt med att kontrollera ditt [!DNL MySQL]-fel i den här [[!DNL MySQL] serverfelmeddelandereferensen](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NEJ - Fortsätt till [steg 15](#step-15).

+++

## Steg 15 {#step-15}

+++**Har du problem med kompositörens korrigeringar?**

a. JA - fortsätt med att konsultera [När du använder en korrigeringsfil tas din plats bort](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down).\
b. NEJ - Fortsätt till [steg 16](#step-16).

+++

## Steg 16 {#step-16}

+++**Har du SQL-databasfel?**

a. JA - Fortsätt med att kontrollera ditt [!DNL MySQL]-fel i den här [[!DNL MySQL] serverfelmeddelandereferensen](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NEJ - Fortsätt till [steg 17](#step-17).

+++

## Steg 17 {#step-17}

+++**Har du [!DNL MySQL] databaslås som inte fungerar eller en [!DNL MySQL] databas som inte svarar?**

a. JA - Fortsätt med att kontrollera om det finns [!DNL MySQL]-deadlocks i den här [Deadlocks in [!DNL MySQL]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/database/deadlocks-in-mysql)-artikeln.\
b. NEJ - Öppna en [supportbiljett](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) om du vill ha mer information.

+++

[Tillbaka till steg 1](#step-1)

Klicka [HÄR](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram) om du vill visa felsökningsflödesschemat för webbplats.

## Relaterad läsning

[Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
