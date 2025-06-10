---
title: 'Fel vid verifiering av autentiseringsuppgifterna för  [!DNL Fastly] '
description: Den här artikeln innehåller en lösning på problemet där en användare får ett fel när inloggningsuppgifterna för  [!DNL Fastly]  valideras.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 838f0c5d55c29d026dc37a8f7e5214b9880a4353
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Fel vid verifiering av autentiseringsuppgifterna för [!DNL Fastly]

I den här artikeln beskrivs hur du löser *Token som upphört*-fel som uppstod vid verifiering av autentiseringsuppgifter för [!DNL Fastly].

Stegen som beskrivs i den här artikeln gäller även om du av säkerhetsskäl måste rotera (bläddra) din [!DNL Fastly] API-token. I dessa fall bör du skicka en Adobe Commerce Support-biljett för att begära en ny [!DNL Fastly] API-token.

## Problem

* Du får ett fel när autentiseringsuppgifterna för [!DNL Fastly] valideras.
* Du misstänker att din [!DNL Fastly]-token kan ha komprometterats, till exempel om den av misstag delats i en supportanmälan eller publicerats på ett offentligt forum.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder): Alla versioner
* Tillägg eller teknik ([!DNL Fastly], [!DNL New Relic] osv.) version [!DNL Fastly]

## Lösning

1. Kontrollera att du har rätt [!DNL Fastly] tjänst-ID och API-token och försök validera igen. Mer information finns i [Testa  [!DNL Fastly] inloggningsuppgifterna](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials) i utvecklardokumentationen.
1. Om verifieringen av inloggningsuppgifterna misslyckas kör du följande kommando för att bekräfta tjänstens status:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Om ovanstående kommando returnerar ett fel som liknar: `{"msg":"Token $TOKEN expired at 2021-09-28T02:03:37Z"}`, skickar du en supportanmälan och begär en ny API-token. Uppdatera konfigurationen i miljön när du har tagit emot din nya token.

   Mer information om hur du skickar in en supportanmälan finns i [Adobe Commerce Help Center User Guide > SUPPORT TICKETS](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) i vår kunskapsbas.

   >[!NOTE]
   >
   >Dela aldrig några lösenord eller giltiga/aktiva API-token direkt i biljetten eftersom vi måste återkalla den aktuella token och generera en ny av säkerhetsskäl.
   >
   >Adobe Commerce Support har åtkomst till tokenerna, så du behöver inte inkludera den här informationen i biljetten.

1. Om kommandot inte returnerar felet kontrollerar du att du kör den senaste versionen av tillägget [!DNL Fastly]. Om du använder en äldre version före 1.2.203 måste du först klicka på **[!UICONTROL Save Config]** innan du kan testa autentiseringsuppgifterna.

## Relaterade läsningar i vår dokumentation för utvecklare:

* [Cloud för Adobe Commerce > [!DNL Fastly] > [!DNL Fastly] tjänstkonto och autentiseringsuppgifter](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly?lang=en#fastly-service-account-and-credentials)

* [Cloud för Adobe Commerce > Konfigurera [!DNL Fastly] > Testa  [!DNL Fastly] inloggningsuppgifterna](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)
