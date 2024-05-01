---
title: 403 fel vid åtkomst till Site-Wide Analysis Tool i Adobe Commerce
description: Den här artikeln innehåller en lösning för när du får 403 fel när du försöker komma åt Site-Wide Analysis Tool på Adobe Commerce.
exl-id: f24fad17-62d6-4a0f-bcba-983c3dbee3d7
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# 403 fel vid åtkomst till Site-Wide Analysis Tool i Adobe Commerce

Den här artikeln innehåller en lösning för när du får 403 fel när du försöker komma åt Site-Wide Analysis Tool på Adobe Commerce.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur 2.4.1 och senare.

## Problem

Du får ett 403-fel när du försöker komma åt analysverktyget för hela webbplatsen.

<u>Steg som ska återskapas:</u>

Logga in på Commerce Admin-panelen och klicka på **Rapporter** > *Systeminsikter* > **Site-Wide Analysis Tool**.

<u>Förväntat resultat:</u>

Du ser verktyget för webbplatsövergripande analys.

<u>Faktiskt resultat:</u>

Du ser: *Fel 403.*


## Lösning

Kontrollera att Site-Wide Analysis Tool har rätt åtkomst till ditt program genom att köra följande kommando i CLI. Ersätt `<store URL>` med din webblänk:

```cURL
curl -sIL -X GET <store URL>/swat/key/index | grep HTTP
HTTP/2 403
```

Utför stegen beroende på vilken svarskod du får.

### 403 Ej tillåten svarskod

Om svarskoden är 403 kan du ha ett skydd för Cloudflare-roboten som blockerar Site-Wide Analysis Tool. Om du vill komma åt verktyget vitlistar du dess IP-adresser:

* 107.23.33.174
* 3.225.9.244
* 3.88.83.85

### Korrigera 200 svarskoder och JSON-utdata

Om svaret är rätt 200-kod och JSON-utdata, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att eskalera problemet med åtkomsten till verktyget för webbplatsövergripande analys.


### 500-svarskod (allvarligt fel)

Om en svarskod är 500 (allvarligt fel) installerar du MDVA-38526-korrigeringen. Använd någon av följande länkar för att hämta korrigeringen, beroende på vilken typ av korrigering du vill ha:

* Adobe Commerce i molninfrastruktur: [MDVA-38526_EE_2.4.1-p1_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_v3.patch.zip)
* Adobe Commerce i molninfrastrukturshanteraren: [MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip)

Korrigeringen gäller för Adobe Commerce i molninfrastrukturversionerna 2.4.1 och senare.

### Svaret är inte JSON

Om svarsutdata inte är JSON, kan det bero på implementeringen av PWA/Headless. Om du använder Headless-implementering ska du uppdatera UPWARD-konfigurationen så att den kringgår begäranden till Adobe Commerce Origin. I Adobe Commerce Admin, under **Lager** > **Konfiguration** > **Allmänt** > **Webb** > **Konfiguration av UPWARD PWA** > **Namn på framsida, Tillåtelselista**, lägga till *swat*.

![Uppåt_konfiguration](assets/upward_pwa.png)

Om du fortfarande inte har tillgång till analysverktyget för hela webbplatsen loggar du in nästa gång på administrationspanelen i Commerce och navigerar till **Rapporter** > *Systeminsikter* > **Site-Wide Analysis Tool**, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Relaterad läsning

* [Handbok för Site-Wide Analysis Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html)
