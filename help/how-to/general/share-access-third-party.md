---
title: Testtips för Adobe Commerce om molninfrastruktur från tredje part
description: Den här artikeln innehåller alternativ för att dela åtkomst med en tredje part för att testa/validera när du har problem med ett tillägg för Adobe Commerce i molninfrastruktur.
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Testtips för Adobe Commerce om molninfrastruktur från tredje part

Den här artikeln innehåller alternativ för att dela åtkomst med en tredje part för att testa/validera när du har problem med ett tillägg för Adobe Commerce i molninfrastruktur.
Lämpliga interna rutiner och krav för datasäkerhet bör följas av er när ni bestämmer hur ni ska ge tredje part tillgång.

## Berörda produkter och versioner:

* Adobe Commerce om molninfrastruktur 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Vilka miljöer som ska användas för testning

Beroende på dina interna säkerhetsstandarder kan du välja att låta tredjepartsfelsökningen utföras i en lokal miljö. Om problemet inte kan reproduceras lokalt kanske du vill ge åtkomst till din molnmiljö. Om du väljer att göra det måste du följa dina interna säkerhetsstandarder. Om du ger åtkomst till någon av dina molnmiljöer måste du se till att din tredje part är säker på vad som kan göras och vilket godkännande som krävs för saker som replikering eller som tillåter kodändringar. Detta är särskilt viktigt för produktionsmiljöer.

## Ge tredje part åtkomst och data

* Ge tredjepartsleverantörer åtkomst till molnmiljön. Relaterade artiklar:

   * [Användarhandbok för Adobe Commerce Help Center > DELAD ÅTKOMST: BEHÖRIGHET FÖR ANDRA ANVÄNDARE ATT FÅ ÅTKOMST TILL DITT KONTO](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access) i vår supportkunskapsbas.
   * [Dela ditt Commerce-konto](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-share) i användarhandboken.

* Skapa en databasdump (eller ge tredjepartsleverantören åtkomst för att göra detta). Det kan göras med CLI eller Commerce Admin. Databasdumpen kommer att förfalska kunddata, så allt de får är kod och produkt-SKU:er, etc., inga egna data/kunddata. Använd [Dela ditt Commerce-konto] (/help/how-to/general/create-database-dump-on-cloud.md) i vår kunskapsbas.
* När testningen är klar måste du se till att återkalla den delade åtkomsten till din molnmiljö, enligt beskrivningen i [Adobe Commerce Help Center User Guide > Återkalla (ta bort delad åtkomst)](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access) i vår kunskapsbas för support.

## Testa bästa praxis

Det vanliga är att felsöka i en lokal miljö. Om problemet inte kan reproduceras lokalt går du till Förproduktion. Den tredje parten kan behöva kontrollera produktionen. Se till att din tredje part är medveten om att de bara ska försöka återskapa problemet i produktion och mellanlagring och att inte göra några kodändringar. Om de behöver göra kodändringar måste de först få ditt tillstånd.

## Relaterad läsning

* [Bästa metoder för att använda tillägg från tredje part i Adobe Commerce](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) i vår kunskapsbas för support.
