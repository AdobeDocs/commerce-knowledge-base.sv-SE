---
title: Adobe Commerce [!DNL Site-Wide Analysis Tool] Vanliga frågor om rapporter
description: Läs mer om [!DNL Site-Wide Analysis Tool], ett proaktivt självbetjäningsverktyg och en central lagringsplats som innehåller detaljerade systeminsikter och rekommendationer för att säkerställa säkerheten och användbarheten för din Adobe Commerce-installation.
exl-id: 7c843d55-9e2c-4b18-8859-0ebad0ae28cf
feature: Best Practices, Saas, Support, Tools and External Services
role: Admin
source-git-commit: 4e327654279095f6523a7cbec77bd2dca57b2034
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Adobe Commerce [!DNL Site-Wide Analysis Tool] Vanliga frågor om rapporter

>[!IMPORTANT]
>
>Träder i kraft den 23 april 2024 [!DNL Site-Wide Analysis Tool] kommer att avvecklas för alla Adobe Commerce lokala kunder.

Den här artikeln innehåller en beskrivning av [!DNL Site-Wide Analysis Tool] Rapportera automatiskt för Adobe Commerce om molninfrastrukturskunder varje månad eller kvartal.

>[!NOTE]
>
>I Adobe Commerce om molninfrastruktur v2.4.1 och senare, [!DNL Site-Wide Analysis Tool] är tillgängligt via Commerce Admin Panel. Därför [!DNL Site-Wide Analysis Tool] Rapporterna kan köras direkt av kunden. Mer information finns i [[!DNL Site-Wide Analysis Tool] stödlinje](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/access.html).

## Vad är [!DNL Site-Wide Analysis Tool]?

[!DNL Site-Wide Analysis Tool] är ett SaaS-program som utför en helhetsanalys av kundens webbplats (punkt-i-tid) (i [!DNL Site-Wide Analysis Tool] -miljö, inte på kundens webbplats). Alla [!DNL Site-Wide Analysis Tool]-relaterad kundplatsinformation samlas in vid förbestämda tidsplaner från var 3: e timme till en gång om dagen. Detta innebär att [!DNL Site-Wide Analysis Tool] analyserar ständigt kundwebbplatsdata för att hitta nya resultat.

## Vad är en [!DNL Site-Wide Analysis Tool] Rapportera?

The [!DNL Site-Wide Analysis Tool] Rapporten innehåller en lista med brister (problem) med självbetjäning, rekommendationer om bästa praxis, som kan skickas till kunder i ett PDF-format via Adobe Commerce supportbiljetsystem.

## Vilken information finns i [!DNL Site-Wide Analysis Tool] Rapportera?

Webbplatsinformationen som finns i [!DNL Site-Wide Analysis Tool] rapporten innehåller följande:

* Söker
   * Översikt, inklusive &#39;Prioritet&#39; för implementeringskorrigeringsordning
   * Sökningsbeskrivning
   * Förvillkor, om sådana finns
   * Effekter på webbplatsen
   * Rotorsak(er)
   * Rekommendationer
* Undantagsloggar
   * Information om loggundantag
   * Datum för senaste förekomst
   * Antal gånger som undantaget inträffar

## Vem får den automatiska månadsvis [!DNL Site-Wide Analysis Tool] rapporter?

För närvarande har kunderna låg [!DNL Site-Wide Analysis Tool] Hälsoindex (vid eller under den för närvarande angivna prestandatröskeln) får en månatlig [!DNL Site-Wide Analysis Tool] Rapportera om deras produktionsmiljö via supportbiljettsystemet.

## Vem får den automatiska kvartalsvis [!DNL Site-Wide Analysis Tool] rapporter?

Alla kunder, oavsett [!DNL Site-Wide Analysis Tool] Hälsoindex, kommer att få en kvartalsvis [!DNL Site-Wide Analysis Tool] Rapportera om deras produktionsmiljö via supportbiljettsystemet.

## Hur levereras rapporter?

[!DNL Site-Wide Analysis Tool] rapporter skickas automatiskt via Adobe Commerce supportbiljettssystem varje månad eller kvartal. [!DNL Site-Wide Analysis Tool] kan också genereras manuellt från [!DNL Site-Wide Analysis Tool] Instrumentpanel och sparad på skrivbordet. Dessa [!DNL Site-Wide Analysis Tool] rapporter kan sedan skickas med e-post som bilagor.
