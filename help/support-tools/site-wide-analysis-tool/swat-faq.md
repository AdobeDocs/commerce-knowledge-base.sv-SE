---
title: Adobe Commerce [!DNL Site-Wide Analysis Tool] Rapportera vanliga frågor
description: Lär dig mer om  [!DNL Site-Wide Analysis Tool], ett proaktivt självbetjäningsverktyg och en central lagringsplats som innehåller detaljerade systeminsikter och rekommendationer för att säkerställa säkerheten och användbarheten för din Adobe Commerce-installation.
exl-id: 7c843d55-9e2c-4b18-8859-0ebad0ae28cf
feature: Best Practices, Saas, Support, Tools and External Services
role: Admin
source-git-commit: 580ad148cd4346868cd9892a1ae9a4d85f73edce
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Vanliga frågor om Adobe Commerce [!DNL Site-Wide Analysis Tool]-rapport

>[!IMPORTANT]
>
>Från och med den 23 april 2024 kommer [!DNL Site-Wide Analysis Tool] att tas bort för alla Adobe Commerce lokala kunder.

Den här artikeln innehåller en beskrivning av [!DNL Site-Wide Analysis Tool]-rapporten som genereras automatiskt för Adobe Commerce på molninfrastrukturskunder på månads- eller kvartalsbasis.

>[!NOTE]
>
>I Adobe Commerce i molninfrastruktur v2.4.1 och senare är [!DNL Site-Wide Analysis Tool] tillgängligt via Commerce Admin Panel. Därför kan [!DNL Site-Wide Analysis Tool] rapporter köras direkt av kunden. Mer information finns i [[!DNL Site-Wide Analysis Tool] handboken](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/access.html).

## Vad är [!DNL Site-Wide Analysis Tool]?

[!DNL Site-Wide Analysis Tool] är ett SaaS-program som utför en kundplatsanalys från början till slut (i [!DNL Site-Wide Analysis Tool] -miljön, inte på kundens webbplats). All [!DNL Site-Wide Analysis Tool]-relaterad kundplatsinformation samlas in i förbestämda scheman från var 3: e timme till en gång om dagen. Det innebär att [!DNL Site-Wide Analysis Tool] hela tiden analyserar kundwebbplatsdata för att hitta några resultat.

## Vad är en [!DNL Site-Wide Analysis Tool]-rapport?

[!DNL Site-Wide Analysis Tool]-rapporten innehåller en lista med resultat (problem) med självbetjäning, rekommendationer om bästa praxis, som kan skickas till kunder i en PDF-form via Adobe Commerce supportbiljettsystem.

## Vilken information ingår i en [!DNL Site-Wide Analysis Tool]-rapport?

Webbplatsinformationen som anges i rapporten [!DNL Site-Wide Analysis Tool] innehåller:

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

## Vem får de automatiska månatliga [!DNL Site-Wide Analysis Tool]-rapporterna?

För närvarande får de kunder som har ett lågt hälsoindex på [!DNL Site-Wide Analysis Tool] (vid eller under det angivna prestandatröskelvärdet) en [!DNL Site-Wide Analysis Tool] -månadsrapport för sin produktionsmiljö via supportbiljettsystemet.

## Vem får de automatiska kvartalsvisa [!DNL Site-Wide Analysis Tool] rapporterna?

Alla kunder, oavsett hälsoindex för [!DNL Site-Wide Analysis Tool], får en [!DNL Site-Wide Analysis Tool]-rapport varje kvartal för sin produktionsmiljö via supportbiljettssystemet.

## Hur levereras rapporter?

[!DNL Site-Wide Analysis Tool] rapporter levereras automatiskt via Adobe Commerce supportbiljettssystem varje månad eller kvartal. [!DNL Site-Wide Analysis Tool] rapporter kan också genereras manuellt från [!DNL Site-Wide Analysis Tool]-instrumentpanelen och sparas på skrivbordet. Dessa [!DNL Site-Wide Analysis Tool] rapporter kan sedan skickas med e-post som bilagor.

>[!NOTE]
>
>När du har tillämpat en rekommendation uppdateras inte rekommendationerna när du genererar en rapport manuellt. Det kan ta några dagar innan den tas bort från [!DNL Site-Wide Analysis Tool Dashboard].
