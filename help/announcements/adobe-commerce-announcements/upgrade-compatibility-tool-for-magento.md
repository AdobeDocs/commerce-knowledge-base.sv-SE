---
title: Upgrade Compatibility Tool 1.1.0 for Adobe Commerce
description: Upgrade Compatibility Tool 1.1.0 är ett kommandoradsverktyg som kontrollerar en Adobe Commerce-instans mot en viss version genom att analysera alla moduler och all kärnkod som är installerade i den. Den returnerar en lista med allvarliga fel, problem och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce.
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Upgrade Compatibility Tool 1.1.0 for Adobe Commerce

Upgrade Compatibility Tool 1.1.0 är ett kommandoradsverktyg som kontrollerar en Adobe Commerce-instans mot en viss version genom att analysera alla moduler och all kärnkod som är installerade i den. Den returnerar en lista med allvarliga fel, problem och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce.

## Nyheter i UCT 1.1.0

Med uppgraderingskompatibilitetsverktyget 1.1.0 får du avsevärda förbättringar, bland annat:

* **Verifiera ändringar av kärnfiler**: Adobe rekommenderar starkt att du inte anpassar kärnproduktkoden. I den här versionen har vi lagt till en kontrollpunkt där kunder och partners kan identifiera eventuella ändringar i kärnkoden för att förstå ändringarnas påverkan snabbt och tidigt. Genom att lägga till det här verktyget i utvecklingsprocessen kan partners och handlare identifiera problem proaktivt, förebygga problem under framtida uppgraderingar och minska den totala ägandekostnaden.
* **Exportera rapporten till en JSON-fil**: Den här förbättringen implementerades efter feedback från communityn. När du kör verktyget exporteras nu information om alla identifierade problem till en JSON-fil så att användarna kan läsa, dela och hantera resultaten utan att behöva köra verktyget igen.
* **Förbättrade VBE-valideringar**: VBE (Vendor Bundled Extensions) är inte en del av Adobe Commerce kärnkod utan testas och stöds av Adobe. Med den här uppdateringen validerar vi nu VBE:er på samma sätt som vi använder för kärnkod. Denna förbättring hjälper användarna att förstå frågor som rör anpassningar och kärnkod/VBE:er tydligt.
* **Ange felkoder**: Vi introducerade felkoder som hjälper användare att identifiera, förstå och lösa problem under en uppgradering. Fel- och varningsmeddelanden ger en tydlig beskrivning och föreslagen lösning.
* **Möjlighet att endast lista kritiska problem**: Med detta kan användare bara fokusera på de problem som är kritiska och som genererar problem under uppgraderingen.
* **Delta-problem mellan två versioner**: med den här förbättringen som föreslagits av våra communitymedlemmar kan UCT-användare få en del av problemen mellan två versioner, vilket gör att de kan fokusera på de nya problemen som introducerats för den målversion de ska uppgradera.

## Vilka versioner kan verktyget jämföra?

Du kan använda verktyget för att jämföra 2.x-versioner.

## Vem kan använda uppgraderingskompatibilitetsverktyget 1.1.0?

Adobe Commerce-kunder.

## Installera uppgraderingskompatibilitetsverktyget 1.1.0

Installationsanvisningar finns i Adobe Commerce: [Upgrade Compatibility Tool > Install](https://devdocs.magento.com/upgrade-compatibility-tool/install.html) i utvecklardokumentationen. Information om krav för att använda verktyget finns i Adobe Commerce: [Upgrade Compatibility Tool](https://devdocs.magento.com/upgrade-compatibility-tool/prerequisites.html) i utvecklardokumentationen.

## Vilket nummer har varje nummer?

Det här är felmeddelandereferensen som ger information om fel som kan inträffa när verktyget för kompatibilitet med uppgradering körs.

Felmeddelandena för verktyget Kompatibilitet för uppgradering är indelade efter nivå (kritiska problem, fel och varningar) och typ (kärnkod, anpassad kod och GraphQL-scheman). Varje typ innehåller följande information:

* Felkod: Felmeddelandets Adobe Commerce-tilldelade identifierare.
* Felbeskrivning: En beskrivning som sammanfattar orsaken till felet.
* Föreslagen felåtgärd: Om det är tillämpligt ger det vägledning om hur du felsöker och löser felet.
* Koderna listas och beskrivs på [referenssidan för felmeddelanden](https://devdocs.magento.com/upgrade-compatibility-tool/errors.html).

## Var kan jag få feedback om verktyget?

Du kan kontakta UCT-teamet på vår [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F) slack channel. Vi ser fram emot att få dina synpunkter och förslag för att förbättra verktyget.

## Relaterad läsning

* Adobe Commerce-blogg: [Introduktion till uppgraderingskompatibilitetsverktyget (Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce: [Kompatibilitetsverktyg för uppgradering](https://devdocs.magento.com/upgrade-compatibility-tool/introduction.html) i utvecklardokumentationen.
