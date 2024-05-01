---
title: Det gick inte att montera beställningen med Authorize.net Sandbox-konto (ett fel uppstod på servern)
description: I den här artikeln finns en korrigering för "*Ett fel uppstod på serverfelmeddelandet*" när en beställning skulle göras med Authorize.Net Direct Post.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Det gick inte att montera beställningen med Authorize.net Sandbox-konto (ett fel uppstod på servern)

I den här artikeln finns en korrigering för &quot;*Ett fel uppstod på servern*&quot; felmeddelande när en beställning görs med Authorize.Net Direct Post.

>[!WARNING]
>
>**Meddelande om borttagning**
>
>På grund av direktivet om betaltjänster [PSD2](https://docs.magento.com/user-guide/v2.3/stores/compliance-payment-services-directive.html) och den fortsatta utvecklingen av många API:er riskerar Authorize.Net att bli föråldrad och inte längre vara kompatibel med säkerhet i framtiden. Därför är den nu föråldrad och vi rekommenderar att du inaktiverar den i din Adobe Commerce-konfiguration och övergår till motsvarande [Commerce Marketplace](https://marketplace.magento.com/extensions.html).
>
>**Den här integreringen har tagits bort från Adobe Commerce 2.4.0 och har tagits bort från de aktuella versionerna av 2.3.**
>
>Mer information om hur du gör en säker övergång från inaktuella betalningsintegreringar finns i vår [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Problem

Placera en order med [Authorize.Net Direct Post](https://docs.magento.com/user-guide/v2.3/payment/authorize-net-direct-post.html) Sandlådekonto orsakar ett felmeddelande:

>>
&quot;Ett fel uppstod på servern. Försök beställa igen&quot;

## Orsak 1: Testläget är aktiverat

Det verkar inte uppenbart, men Authorize.net:s **Testläge** inställningen måste anges till **Nej** även när du testar med sandlådekontot.

## Lösning 1: inaktivera testläge

1. Gå till **Lager** > **Konfiguration** > **Försäljning** > **Betalningsmetoder** > **Andra betalningsmetoder** > **Authorize.net Direct Post**.
1. Ange **Testläge** till Nej (avmarkera) **Använd systemvärde** väljer du&quot;Nej&quot; på menyn).
1. Klicka **Spara konfiguration**.

![authze-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Orsak 2: Felaktiga URL:er

Authorize.net kan innehålla felaktiga URL-adresser för de viktiga Authorize.Net-resurserna.

## Lösning 2: Ange korrekta URL:er

* **Gateway-URL:**   `https://test.authorize.net/gateway/transact.dll`
* **URL för transaktionsinformation:**   `https://apitest.authorize.net/xml/v1/request.api`
* **API-referens:**   `https://developer.authorize.net/api/reference/`

## Om inget hjälpte: hämta felsökningsinformation

Om en beställning med Authorize.net misslyckas med en icke-informativ *&quot;Något gick fel&quot;* fel, kontrollera Adobe Commerce `debug.log`.

### Transact.dll

Om `debug.log` är tom, kontrollera **transact.dll** svar i webbläsarens konsol:

1. Öppna konsolen.
1. Innan du lägger en order går du till **Nätverk** och markera **Bevara logg**.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Filtrera svar efter **transact.dll** för att visa ett svarsmeddelande med ett möjligt fel.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
