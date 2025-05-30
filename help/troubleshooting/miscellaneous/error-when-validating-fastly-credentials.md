---
title: Fel vid validering av snabbinloggningsuppgifterna
description: I den här artikeln finns en lösning på problemet där användaren får ett fel vid valideringen av snabbinloggningsuppgifterna.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Fel vid validering av snabbinloggningsuppgifterna

I den här artikeln finns en lösning på problemet där användaren får ett fel vid valideringen av snabbinloggningsuppgifterna.

## Problem

Användaren får ett fel vid valideringen av snabbinloggningsuppgifterna.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder): Alla versioner
* Tilläggs- eller teknikversion (snabbt, New Relic osv.) snabbt

## Lösning

1. Kontrollera att du har rätt ID och API-token för tjänsten och försök validera igen. Mer information finns i [Testa snabbinloggningsuppgifterna](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials) i utvecklardokumentationen.
1. Om verifieringen av inloggningsuppgifterna misslyckas kör du följande kommando för att bekräfta tjänstens status:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Om ovanstående kommando returnerar ett fel som liknar: *{&quot;msg&quot;:&quot;Token $TOKEN gick ut 2021-09-28T02:03:37Z&quot;}* skickar du en supportanmälan för att begära en ny API-token.

   Mer information om hur du skickar in en supportanmälan finns i [Adobe Commerce Help Center User Guide > SUPPORT TICKETS](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) i vår kunskapsbas.

   >[!NOTE]
   >
   >Dela aldrig några lösenord eller giltiga/aktiva API-token direkt i biljetten eftersom vi måste återkalla den aktuella token och generera en ny av säkerhetsskäl.

1. Om kommandot inte returnerar felet kontrollerar du att du kör den senaste versionen av tillägget [!DNL Fastly]. Om du använder en äldre version före 1.2.203 måste du först klicka på **[!UICONTROL Save Config]** innan du kan testa autentiseringsuppgifterna.

## Relaterade läsningar i vår dokumentation för utvecklare:

* [Cloud för Adobe Commerce > Snabbt > Snabbt tjänstkonto och autentiseringsuppgifter](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/cdn/fastly#fastly-service-account-and-credentials)

* [Cloud för Adobe Commerce > Konfigurera snabbt > Testa snabbinloggningsuppgifterna](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials)
