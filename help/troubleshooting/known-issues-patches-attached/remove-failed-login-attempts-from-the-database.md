---
title: Ta bort misslyckade inloggningsförsök från databasen
description: I den här artikeln beskrivs hur du tar bort tidigare misslyckade inloggningsuppgifter från Adobe Commerce lokala platser och Adobe Commerce i molninfrastruktursdatabasen. För version 2.2.10+ och 2.3.3+ behöver du bara köra det bifogade skriptet. För äldre versioner 2.3.0-2.3.2-p2 måste du tillämpa en patch för att stoppa loggningen och köra det bifogade skriptet för att ta bort tidigare misslyckade inloggningsuppgifter.
exl-id: 0d7e3674-3563-414f-86a2-297eb8104099
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Ta bort misslyckade inloggningsförsök från databasen

>[!NOTE]
>
>Den här artikeln uppdaterades den 13 april 2020 med ett nytt skript som heter DB\_CLEANUP\_SCRIPT\_v2. Använd det bifogade DB\_CLEANUP\_SCRIPT\_v2 för att rensa tidigare misslyckade inloggningsdata i ytterligare tabeller. Du måste använda DB\_CLEANUP\_SCRIPT\_v2, även om du har kört DB\_CLEANUP\_SCRIPT\_v1 tidigare, för att se till att fler tabeller rensas.

I den här artikeln beskrivs hur du tar bort tidigare misslyckade inloggningsuppgifter från Adobe Commerce lokala platser och Adobe Commerce i molninfrastruktursdatabasen. För version 2.2.10+ och 2.3.3+ behöver du bara köra det bifogade skriptet. För äldre versioner 2.3.0-2.3.2-p2 måste du tillämpa en patch för att stoppa loggningen och köra det bifogade skriptet för att ta bort tidigare misslyckade inloggningsuppgifter.

## **Berörda produkter och versioner**

* Problemet berör Magento Open Source, Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.2.x, 2.3.x och tidigare versioner.
* Adobe Commerce 1.x-distributioner påverkas inte.

## Problem

2019 rapporterades ett fel till Adobe Commerce som gjorde att misslyckade inloggningsförsök kunde loggas i en databas i Adobe Commerce 2.3.x och 2.2.x. Som svar innehöll Adobe Commerce en korrigering av problemet i Adobe Commerce 2.3.3 och 2.2.10 (släppt i oktober 2019). Även om korrigeringen för det felet stoppade loggningen av misslyckade inloggningsförsök finns det fortfarande information som samlats in innan dessa aktuella versioner uppdaterades. Den senaste korrigeringen rensar den information om inloggningsförsök som tidigare loggats, om sådan finns.   CVE-2019-8118 beskrivs och spåras i [Vanliga sårbarheter och exponeringar](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8118).

## Lösning

Om du behöver använda det bifogade skriptet och korrigeringsfilen, eller bara skriptet, beror på vilken version av Adobe Commerce du har:

**Adobe Commerce och Magento Open Source version 2.3.0-2.3.2-p2**

För dessa versioner måste du tillämpa korrigeringen och köra det bifogade databasrensningsskriptet för att avsluta den fortsatta loggningen och ta bort loggar.

1. Kör kompositörens korrigering för att stoppa loggningen. Den här korrigeringen är kopplad till artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk [CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip). Instruktioner om hur du tillämpar korrigeringen finns i [Använda en kompositkorrigering från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

1. Kör nu skriptet för att rensa databasen för tidigare misslyckade inloggningsförsök. Skriptet är kopplat till artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk: [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Mer information finns i avsnittet [**Så här kör du skriptet**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script).

**Adobe Commerce och Magento Open Source version 2.3.3 och senare/2.2.10 och senare**<br>
Endast för dessa versioner kör du nedanstående skript för att rensa gamla loggar (loggningen avslutades tidigare för dessa versioner genom en korrigering som släpptes i oktober 2019). Skriptet är kopplat till artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk: [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Instruktioner finns i avsnittet [**Så här kör du skriptet**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) i vår kunskapsbas för support.

**Köra skriptet**

Följ instruktionerna nedan för att köra skriptet:

1. Placera `DB_CLEANUP_SCRIPT_v2.php` i rotkatalogen för Adobe Commerce- eller Magento Open Source-installationen (i samma katalog som appen som innehåller `app/bootstrap.php`).
1. Kör det här kommandot i terminalen: `php DB_CLEANUP_SCRIPT_v2.php` så startas databasrensningen.

Om du stöter på problem när du kör skriptet kan du [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) eller skicka ett e-postmeddelande till oss på [security@magento.com](mailto:security@magento.com).

**Bifogade filer**

[CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)

[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)
