---
title: Vanliga frågor om Adobe Commerce Security Scan Tool
description: I den här artikeln besvaras några vanliga frågor och svar om Adobe Commerce säkerhetssökningsverktyg.
exl-id: 380ce617-e3d9-491b-b425-8489abd3c541
feature: Compliance
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# Vanliga frågor om Adobe Commerce Security Scan Tool

I den här artikeln besvaras några vanliga frågor och svar om Adobe Commerce säkerhetssökningsverktyg.

## Vad är verktyget för säkerhetsgenomsökning och vem är det avsett för? {#what-is-the-magento-security-scan-tool-and-who-is-it-written-for}

Verktyget för säkerhetsgenomsökning är ett kostnadsfritt verktyg som är tillgängligt för våra handlare, utvecklare och den personal som de utser som ansvariga för att övervaka deras sajter med avseende på säkerhetsrisker. Programmet kan aktivt och effektivt upptäcka skadlig kod i butiker och meddela handlarna om det finns några säkerhetsrisker, skadlig programvara eller hot.

## Är verktyget för säkerhetsgenomsökning tillgängligt för alla Adobe Commerce-handlare? {#is-magento-security-scan-tool-available-to-all-magento-merchants}

Ja, verktyget för säkerhetsgenomsökning är tillgängligt för alla handlare i Adobe Commerce och Magento Open Source.

## Kan någon skanna min webbplats med verktyget för säkerhetsgenomsökning? {#can-anyone-scan-my-site-with-the-magento-security-scan-tool}

Nej, en handlare binder sin webbplats till sitt Adobe Commerce-konto när de begär en skanning via en token. Detta är unikt per plats.

## Kan verktyget skanna icke-Adobe Commerce-sidor på min webbutik? {#can-the-tool-scan-non-magento-pages-on-my-webstore}

Säkerhetssökningsverktyget är utformat för att söka efter säkerhetsluckor i Adobe Commerce-domäner. Skanning av icke-Adobe Commerce-sidor efter säkerhetsluckor med verktyget för säkerhetsgenomsökning kan leda till otillförlitliga resultat. Vi rekommenderar starkt att våra handlare inte använder verktyget för säkerhetsgenomsökning för att skanna sidor som skapats av andra plattformar som inte kommer från Adobe Commerce.

## Kan jag utesluta specifika säkerhetstester från skanningsverktyget? {#can-i-exclude-specific-security-tests-from-magento-scan-tool}

Handläggarna för säkerhetsgenomsökningsverktyget kan inte utesluta specifika säkerhetstester från säkerhetsgenomsökningsverktyget för Adobe Commerce. Varje säkerhetstest för verktyget för säkerhetsgenomsökning är skrivet för att hjälpa handlarna att identifiera säkerhetsrisker, skadlig programvara och hot.

## Vad kostar det? {#what-does-it-cost}

Verktyget för säkerhetsgenomsökning är kostnadsfritt. Handlarna måste godkänna en ansvarsfriskrivning som befriar Adobe Commerce från ansvar baserat på resultatet av säkerhetsgenomgången eller webbplatsens konfiguration.

## Hur fungerar verktyget för säkerhetsgenomsökning? {#how-does-the-magento-security-scan-tool-work}

Verktyget för säkerhetsgenomsökning är webbaserat och nås från handlarens Adobe Commerce-konto online ([account.magento.com](https://account.magento.com/)). Säkerhetssökningen utförs över både HTTP och HTTPS. Den söker efter kända säkerhetsproblem och identifierar saknade Adobe Commerce-patchar och uppdateringar.

## Hur registrerar jag mig för att använda verktyget för säkerhetsgenomsökning? {#how-do-i-sign-up-to-use-the-magento-security-scan-tool}

Handlare kan registrera sig för att använda verktyget för säkerhetsgenomsökning för att skanna sina webbutiker från sitt Adobe Commerce-konto ([account.magento.com](https://account.magento.com)). Följ länken för att registrera dig för verktyget för säkerhetsgenomsökning [här](https://account.magento.com/scanner/dashboard/?_ga=2.83981338.267715797.1615821601-2099431409.1611073686).

## Vad gör jag om jag stöter på ett falskt positivt resultat i skanningsrapporten? {#what-do-i-do-if-i-come-across-a-false-positive-in-the-scan-report}

Vi rekommenderar våra handlare att undersöka alla misslyckade sökningar och vidta lämpliga åtgärder för att lösa sådana problem. Om handlarna efter en utredning får ett inskannat resultat som verkar vara falskt positivt ber vi handlaren att meddela Adobe om att vidta lämpliga åtgärder.

Om du vill skicka in en falskt positiv rapport anger du en biljett med Adobe Commerce handlarsupport så att vi kan utvärdera det falska positiva meddelandet, göra nödvändiga ändringar och/eller lämna rekommendationer för att undvika att få sådana meddelanden i framtiden. Merchants kan också rapportera en falsk positiv bild genom att skicka e-post till oss på [securityscan@magento.com](mailto:securityscan@magento.com).
