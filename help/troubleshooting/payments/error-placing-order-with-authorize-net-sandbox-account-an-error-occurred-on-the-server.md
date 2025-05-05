---
title: Det gick inte att montera beställningen med Authorize.net Sandbox-konto (ett fel uppstod på servern)
description: I den här artikeln finns en korrigering för "*Ett fel uppstod på serverfelmeddelandet*" när en beställning skulle göras med Authorize.Net Direct Post.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Det gick inte att montera beställningen med Authorize.net Sandbox-konto (ett fel uppstod på servern)

I den här artikeln finns en korrigering för *Ett fel inträffade på serverfelmeddelandet* när en beställning gjordes med Authorize.Net Direct Post.

>[!WARNING]
>
>**Meddelande om borttagning**
>
>På grund av betaltjänstdirektivet [PSD2](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive) och den fortsatta utvecklingen av många API:er riskerar Authorize.Net att bli inaktuell och inte längre kompatibel med säkerhet i framtiden. Därför är den nu föråldrad och vi rekommenderar att du inaktiverar den i din Adobe Commerce-konfiguration och övergår till motsvarande [Commerce Marketplace-tillägg](https://marketplace.magento.com/extensions.html).
>
>**Den här integreringen har tagits bort från Adobe Commerce 2.4.0 och har tagits bort från de aktuella versionerna av 2.3.**
>
>Mer information om hur du gör en säker övergång från inaktuella betalningsintegreringar finns i [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Problem

Om du placerar en order med sandlådekontot [Authorize.Net Direct Post](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/error-placing-order-with-authorize-net-sandbox-account-an-error-occurred-on-the-server) visas ett felmeddelande:

&#x200B;>>
&quot;Ett fel uppstod på servern. Försök beställa igen&quot;

## Orsak 1: Testläget är aktiverat

Det verkar inte uppenbart, men inställningen **Testläge** för Authorize.net måste anges till **Nej** även när du testar med sandlådekontot.

## Lösning 1: inaktivera testläge

1. Gå till **Butiker** > **Konfiguration** > **Försäljning** > **Betalningsmetoder** > **Andra betalningsmetoder** > **Authorize.net Direktinlägg**.
1. Ange **Testläge** till Nej (avmarkera **Använd systemvärde** och välj sedan Nej på menyn).
1. Klicka på **Spara konfiguration**.

![authorized-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Orsak 2: Felaktiga URL:er

Authorize.net kan innehålla felaktiga URL-adresser för de viktiga Authorize.Net-resurserna.

## Lösning 2: Ange korrekta URL:er

* **Gatewayens URL:**   `https://test.authorize.net/gateway/transact.dll`
* **URL för transaktionsinformation:**   `https://apitest.authorize.net/xml/v1/request.api`
* **API-referens:**   `https://developer.authorize.net/api/reference/`

## Om inget hjälpte: hämta felsökningsinformation

Om en beställning med Authorize.net misslyckas med ett icke-informativt fel av typen *&quot;Något gick fel&quot;* bör du kontrollera Adobe Commerce `debug.log`.

### Transact.dll

Om `debug.log` är tom kontrollerar du svaret **transact.dll** i webbläsarens konsol:

1. Öppna konsolen.
1. Gå till fliken **Nätverk** och välj **Bevara logg** innan du gör en beställning.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Filtrera svar efter **transact.dll** för att visa ett svarsmeddelande med ett möjligt fel.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
