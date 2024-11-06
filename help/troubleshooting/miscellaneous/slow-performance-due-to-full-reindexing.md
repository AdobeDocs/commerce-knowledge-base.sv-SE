---
title: Långsam prestanda på grund av fullständig omindexering
description: Den här artikeln innehåller en korrigering för dålig prestanda på grund av fullständig omindexering (där data i de indexeringsrelaterade databastabellerna uppdateras).
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Långsam prestanda på grund av fullständig omindexering

Den här artikeln innehåller en korrigering för dålig prestanda på grund av fullständig omindexering (där data i de indexeringsrelaterade databastabellerna uppdateras).

## Berörda versioner och produkter

* Adobe Commerce i molninfrastruktur 2.x.x
* Adobe Commerce lokal 2.x.x

### Problem

Konstant tömning och indexåterskapande är några av orsakerna till prestandaförsämring. Dessutom lägger konstant, fullständig omindexering till lås i tabeller, vilket gör att webbplatsen fungerar mycket långsammare än förväntat.

### Orsak

Åtgärder som kan ge fullständig omindexering utfördes från administratören:

* Spara produktattribut
* Spara webbplats-/butiksvy
* Butikskonfiguration

>[!NOTE]
>
>Dessa åtgärder bör köras utanför kontorstid för att säkerställa att dessa åtgärder inte påverkar prestanda under kontorstid.

[Tredjepartstillägg](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) kan också orsaka fullständig omindexering. Fullständig omindexering kan också köras manuellt från CLI. Så här tar du reda på om du har index som omindexeras och som kan ge sämre prestanda:

1. Utför den här frågan för att hitta indexerare som har indexerats om helt under de senaste 15 minuterna:

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   Ett indexerarnamn i utdata innebär att indexeraren har indexerats om minst en gång under de senaste 15 minuterna.

1. Om du har hittat fullständig omindexering ofta bör du ta reda på följande:
   * Vem gör detta manuellt från CLI:n?
   * Vad tredjepartsmodulen gör omindexeringen
   * Vilken tredjepartsmodul markerar indexerare som *Ogiltig*

### Lösning

Kör bara omindexering när det behövs. Om du vill veta mer går du till [Konfigurera indexerare](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) i utvecklardokumentationen. En allmän rekommendation och bästa praxis är att tillåta den partiella omindexeringsmekanismen att hantera omindexering av data utan manuell åtgärd från en handlare. All omindexering ska göras med den inbyggda Adobe Commerce-funktionen (Mview). Mview utför partiell omindexering, vilket är det mest effektiva sättet att indexera om data. Mer information om Mview finns i [Indexeringsöversikt: Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) i utvecklardokumentationen.

## Relaterad läsning

* [Indexeringsöversikt: Så här indexerar du om ](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) i utvecklardokumentationen.
* [Ovaliderat cacheminne orsakar en försämring av svarstiden](/help/troubleshooting/miscellaneous/invalidated-cache-causes-response-time-degradation.md) i vår kunskapsbas för support.
