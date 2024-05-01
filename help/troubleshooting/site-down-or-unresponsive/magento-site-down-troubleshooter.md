---
title: Felsökning av Adobe Commerce webbplats ned
description: Klicka på varje fråga för att visa svarsinformationen i varje steg i felsökaren.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Felsökning av Adobe Commerce webbplats ned

Klicka på varje fråga för att visa svarsinformationen i varje steg i felsökaren.

## Steg 1 {#step-1}

+++**Gör <https://status.adobe.com> visar du några problem?**

a. JA - Om du markerade [Status för Adobe Magento](https://status.adobe.com/products/3350) och det visade ett problem, öppna en [Supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för vidare utredning.\
b. NEJ - Om du markerade [Status för Adobe Magento](https://status.adobe.com/products/3350) och det inte visade på något problem, gå vidare till [Steg 2](#step-2).

+++

## Steg 2 {#step-2}

+++**Visar http://status.fastly.com några problem?**

a. JA - Om du markerade [Snabb status](https://status.fastly.com/) och det visade ett problem, öppna en [Supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för vidare utredning.\
b. NEJ - Om du markerade [Snabb status](https://status.fastly.com/) och det inte visade på något problem, gå vidare till [Steg 3](#step-3).

+++

## Steg 3 {#step-3}

+++**Kontrollera webbplatsen i en webbläsare. Får du en 200-kod (OK)?**

Kontrollera felkoder i **Firefox**: Klicka på **Öppna meny** ikon > **Webbutvecklare** > **Växla verktyg** > **Nätverk** tab > **Alla** filter > **Status** kolumn. Kontrollera felkoder i **Krom**: Klicka på **Öppna meny** ikon > **Fler verktyg** > **Utvecklarverktyg** > **Nätverk** tab > **Alla** filter > **Status** kolumn.

a. JA - Öppna en [Supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för vidare utredning.\
b. NEJ - Fortsätt till [Steg 4](#step-4).

+++

## Steg 4 {#step-4}

+++**Vilken webbplatsfelkod fick du?**

a. Felkod 500 - Kontrollera loggen för `/var/log/platform/`. Om dessa data inte utgör problemet för dig kan du öppna en [Supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och inkludera den felsökningsinformation som du hittills har fått för ytterligare utredning.

b. Felkod 503 - Kontrollera loggen för `var/reports`. Om dessa data inte utgör problemet för dig kan du öppna en [Supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och inkludera den felsökningsinformation som du hittills har fått för ytterligare utredning.

c. Error Code 404 - Run the following query: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Om frågan returnerar en tabell, var `update_exists` värdet är &quot;0&quot;, se [Fel 404 på alla sidor, butiker och administratörer på grund av problem med Content Staging](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md) artikel. I alla andra fall går du vidare till [Steg 5](#step-5).

d. Andra felkoder - gå till [Steg 5](#step-5).

+++

## Steg 5 {#step-5}

+++**Är platsen långsam, eller har hög serverbelastning, hög processorbelastning, långsam behandling av begäranden eller avbrott i MySQL eller Redis?**

a. JA - Fortsätt med steg för [Söker efter DDOS-attacker från CLI](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md).\
b. NEJ - Kontrollera loggar för `/var/log/exception.log` och `/var/log/deploy.log`, och om dessa data inte utgör problemet för dig går du vidare till [Steg 6](#step-6).

+++

## Steg 6 {#step-6}

+++**Har du distributionsfel eller distributionsfel?**

a. JA - Fortsätt till [Steg 13](#step-13).\
b. NEJ - Fortsätt till [Steg 7](#step-7).

+++

## Steg 7 {#step-7}

+++**Har du fel i Elasticsearch?**

a. JA - Fortsätt med steg för [kontrollera Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html).\
b. NEJ - Fortsätt till [Steg 8](#step-8).

+++

## Steg 8 {#step-8}

+++**Har din MySQL-databas långsamma frågor eller felaktiga frågor?**

a. JA - Fortsätt med [Kontrollera långsamma frågor och processer som tar för lång tid i MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md) och kontrollera frågestrukturen i detta [MySQL-frågekurs](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NEJ - Fortsätt till [Steg 9](#step-9).

+++

## Steg 9 {#step-9}

+++**Är ditt statiska innehåll inte tillgängligt?**

a. JA - fortsätt med att läsa [Kontrollera statiskt innehåll](https://support.magento.com/hc/en-us/articles/360031624091) artikel.\
b. NEJ - Fortsätt till [Steg 10](#step-10).

+++

## Steg 10 {#step-10}

+++**Ser du allvarliga PHP-fel i dina loggar?**

a. JA - fortsätt med rådgivning [Vanliga PHP-allvarliga fel och lösningar](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md).\
b. NEJ - Fortsätt till [Steg 11](#step-11).

+++

## Steg 11 {#step-11}

+++**Ser du Redis-fel?**

a. JA - Fortsätt med steg till [verifiera att Redis körs](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify) och for [Redis-felsökning](https://redis.io/topics/problems).\
b. NEJ - Fortsätt till [Steg 12](#step-12).

+++

## Steg 12 {#step-12}

+++**Ser du indexeringsfel?**

a. JA - Om indexet är låst av en annan process, se [Index är låst av en annan process](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md). Om du har andra indexeringsfel öppnar du en [Supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för vidare utredning.\
b. NEJ - Öppna en [Supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för vidare utredning.

+++

## Steg 13 {#step-13}

+++**Har du problem med dina anpassade moduler?**

a. JA - fortsätt att läsa [Allmän felsökningshjälp för anpassad modul](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md).\
b. NEJ - Fortsätt till [Steg 14](#step-14).

+++

## Steg 14 {#step-14}

+++**Har du fel efter krokarna?**

a. JA - Fortsätt med att kontrollera MySQL-felet i detta [Felmeddelandereferens för MySQL-server](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NEJ - Fortsätt till [Steg 15](#step-15).

+++

## Steg 15 {#step-15}

+++**Har du problem med dispositionspatchar?**

a. JA - fortsätt med rådgivning [När du använder en korrigeringsfil tar det längre tid att lägga på webbplatsen](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md).\
b. NEJ - Fortsätt till [Steg 16](#step-16).

+++

## Steg 16 {#step-16}

+++**Har du SQL-databasfel?**

a. JA - Fortsätt med att kontrollera MySQL-felet i detta [Felmeddelandereferens för MySQL-server](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NEJ - Fortsätt till [Steg 17](#step-17).

+++

## Steg 17 {#step-17}

+++**Har du dödläge för MySQL-databasen eller en MySQL-databas som inte svarar?**

a. JA - Fortsätt med att kontrollera om det finns döda MySQL-lås i detta [Deadlocks in MySQL](/help/troubleshooting/database/deadlocks-in-mysql.md) artikel.\
b. NEJ - Öppna en [Supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för vidare utredning.

+++

[Tillbaka till steg 1](#step-1)

Klicka [HÄR](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md) om du vill visa felsökningsflödesschemat för webbplats.
