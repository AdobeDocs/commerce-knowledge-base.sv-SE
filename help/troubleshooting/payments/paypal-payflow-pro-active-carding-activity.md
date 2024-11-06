---
title: PayPal Payflow Pro - aktiv kodningsaktivitet
description: UPPDATERAD 2 april 2019
exl-id: 9fe73788-5b67-445a-9b0d-86489125d271
feature: Cache, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# PayPal Payflow Pro - aktiv kodningsaktivitet

UPPDATERAD 2 april 2019

Integreringen av PayPal Payflow Pro i Adobe Commerce är inriktad på kundvagnsaktiviteter, där angripare försöker genomföra hundratals transaktioner på USD 0 med stulna kreditkort för att kontrollera kortets giltighet.

Aktiviteten avser för närvarande versioner av denna Payflow Pro-integration som ingick i Adobe Commerce 2.1.x, 2.2.x, 2.3.x för Magento Open Source och Commerce (lokalt och molnet). Kodningsaktiviteten är en naturlig del av sättet som Payflow Pro är integrerat i kundvagnar.

>[!NOTE]
>
>Vi har tagit fram nya Composer-paket för att lägga till Google reCAPTCHA eller CAPTCHA i Payflow Pro-formuläret. Vi rekommenderar att du installerar dessa paket på alla versioner och utgåvor av Adobe Commerce.

Problemet berör följande Adobe Commerce-versioner:

* Adobe Commerce lokalt v2.1.x, 2.2.x, 2.3.x
* Adobe Commerce i molninfrastruktur v2.1.x, 2.2.x, 2.3.x

## Problem

Symtomen på dessa attacker är bland annat:

* Ditt PayPal Payflow Pro-konto visar hundratals bedrägliga transaktioner som identifierats
* PayPal kan avbryta ett Payflow Pro-konto på grund av inkommande bedrägeri och ta ut betydande avgifter

## Lösning

För att skydda dig mot dessa attacker rekommenderar vi att du lägger till Google reCAPTCHA (rekommenderas) eller CAPTCHA i utcheckningsformuläret för Payflow Pro. Detta inkluderar installation av Composer-paket och konfigurering av Google reCAPTCHA eller CAPTCHA i Commerce Admin.

### Installera paket

Adobe har skapat två paketalternativ för att lägga till Google reCAPTCHA och/eller CAPTCHA i utcheckningsformuläret Payflow Pro. Om du installerar ett av dessa paket uppdateras de aktuella installationerna och ett alternativ läggs till som kan förbättra säkerheten i utcheckningsformuläret för Payflow Pro.

Dessa paket är kompatibla med följande Adobe Commerce-distributioner och -versioner:

Adobe Commerce (alla distributionsmetoder) och Magento Open Source 2.1.x, 2.2.x, 2.3.x

Installationen kräver CLI-kommandon i din Adobe Commerce-instans. Utvecklarhjälp kan behövas.

>[!NOTE]
>
>Vi rekommenderar att du installerar och konfigurerar Google reCAPTCHA förutom att installera alla relevanta uppdateringar av Payflow Pro-utcheckningsformulär. Det här alternativet ger en osynlig kontroll och flera konfigurationsalternativ.

#### Installera Google reCAPTCHA och uppdatera checkout-formulär

Paketet `magento/module-paypal-recaptcha` innehåller integrering med Google reCAPTCHA och uppdateringar av betalningsformulär för Payflow Pro. Även om du har installerat och konfigurerat modulen reCAPTCHA rekommenderar vi att du installerar det här paketet.

Kör följande kommandon för att installera det.

**För Adobe Commerce lokalt:**

```bash
composer require magento/module-paypal-recaptcha
bin/magento module:enable Magento_PaypalReCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**För Adobe Commerce om molninfrastruktur:**

1. Kör följande kommando:

   ```bash
   composer require magento/module-paypal-recaptcha
   ```

1. Verkställ och skicka ändringar:

   ```bash
   git add -A && git commit -m "Install Google reCAPTCHA"    git push origin %branch_name%
   ```

1. Vänta tills distributionen är klar.

#### Installera uppdateringar av utcheckningsformulär för CAPTCHA

Paketet `magento/module-paypal-captcha` innehåller integration med Adobe Commerce CAPTCHA-modulen.

Installera den genom att köra följande kommandon:

**För Adobe Commerce lokalt:**

```bash
composer require magento/module-paypal-captcha
bin/magento module:enable Magento_PaypalCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**För Adobe Commerce om molninfrastruktur:**

1. Kör följande kommando:

   ```bash
   composer require magento/module-paypal-captcha
   ```

1. Verkställ och skicka ändringar:

   ```bash
   git add -A && git commit -m "Install CAPTCHA"    git push origin %branch_name%
   ```

1. Vänta tills distributionen är klar.

### Konfigurera Google reCAPTCHA eller CAPTCHA

När du har installerat paketet konfigurerar du Google reCAPTCHA (rekommenderas) eller CAPTCHA enligt beskrivningen i följande dokument:

* [Google reCAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-google-recaptcha) i vår användarhandbok.
* [CAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-captcha) i vår användarhandbok.

Det nya alternativet för utcheckningsformulär är:

* Google reCAPTCHA: Använd i betalningsformuläret PayPal Payflow Pro
* CAPTCHA: Payflow Pro

## Stöd och kontakter för PayPal

Kontakta PayPal Payflow Merchant Support om du vill veta mer om bedrägeriskyddstjänster. Du kan begära att PayPal-supportteamet aktiverar [filtren för grundläggande bedrägeriskyddstjänster](https://developer.paypal.com/api/nvp-soap/payflow/fraud-protection/) så att du kan ha så stor kontroll som möjligt över betalningar, så att du automatiskt kan neka betalningar som sannolikt leder till bedrägliga transaktioner och acceptera betalningar som vanligtvis inte är något problem. Observera att när du väl har aktiverat PayPal-filtren för bedrägeriskydd kan det ta upp till två timmar att kvitta transaktionerna.

>[!NOTE]
>
>Mer information finns i PayPals kB [&quot;Adobe har kontaktat mig angående min Payflow Pro-integrering. Vad behöver jag göra?&quot;](https://www.paypal.com/us/smarthelp/article/ts2242).

**Supportinformation för PayPal Payflow Merchant**

Betalflödeshanteringarnas arbetstider är måndag till fredag från 07:00 till 08:00 CST. Du kan kontakta Payflow Merchant Support för att få hjälp via telefon eller mejl:

* Telefon: 1-888-883-9770 (Välj prompt 2)
* Internationella kunder: 0200-810 329
* E-post: [payflow-support@paypal.com](mailto:payflow-support@paypal.com)

Stöd för Australien

* Måndag-fredag 08:00 - 19:00 (AU-tid)
* Telefon: +61 2 8288 0198
* E-post: [gateway-ausupport@paypal.com](mailto:gateway-ausupport@paypal.com)
