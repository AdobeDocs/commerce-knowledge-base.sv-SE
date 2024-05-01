---
title: Felsök hur du skapar en beställningssida i [!UICONTROL CSP] begränsat läge
description: I den här artikeln förklaras felen med att skapa en order på admin-sidan när begränsat CSP-läge är aktiverat, och här beskrivs lösningar på felen.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Felsök hur du skapar en beställningssida i [!UICONTROL CSP] begränsat läge

I den här artikeln beskrivs förklaringar och korrigeringar för Adobe Commerce 2.4.7-problem när en beställning skapas på Admin-sidan med **[!UICONTROL CSP restricted mode]** är *Aktiverad*, med &quot;*Avvisad körning av textbundet skript eftersom det bryter mot följande direktiv om säkerhetsprincip för innehåll: &quot;script-src ...*&quot; i webbläsarkonsolloggen.

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur, Adobe Commerce lokalt och Magento Open Source:

* 2.4.7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Problem - administratör **skapa order** sidan är skadad eller inte kan läsas in

Administratören **skapa order** sidan är skadad eller inte kan läsas in, med &quot;*Avvisad körning av textbundet skript eftersom det bryter mot följande direktiv om säkerhetsprincip för innehåll: &quot;script-src ...*&quot; i webbläsarkonsolloggen.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Skapa en ny order.

<u>Förväntade resultat</u>:

Administratören **skapa order** sidan läses in helt normalt.

<u>Faktiska resultat</u>:

Administratören **skapa order** sidan är tom eller så saknas komponenter. Följande [!DNL JS] fel visas i webbläsarkonsolloggen: &quot;*Avvisad körning av textbundet skript eftersom det bryter mot följande direktiv om säkerhetsprincip för innehåll: &quot;script-src ...*&quot;

### Orsak

I Adobe Commerce och Magento Open Source, version 2.4.7 och senare, **[!UICONTROL CSP]** är konfigurerad i `restrict-mode`, som standard, för betalningssidor i butiks- och administrationsområdet, och i `report-only` läge för alla andra sidor.
Motsvarande **[!UICONTROL CSP]** rubriken innehåller inte `unsafe-inline` nyckelord i `script-src` direktiv för betalningssidor. Dessutom, endast [!DNL whitelisted] textbundna skript tillåts.

### Lösning

Användare kan se webbläsarfel på grund av att vissa skript blockeras på grund av [!UICONTROL CSP]:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Du måste antingen</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de blockerade skripten med `SecureHtmlRenderer` klassen.
1. Använd `CSPNonceProvider` för att tillåta att skript körs.
Adobe Commerce och Magento Open Source 2.4.7 och senare innehåller en **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] leverantör för att underlätta generering av unika [!DNL nonce] strängar för varje begäran. Dessa [!DNL nonce] strängarna kopplas sedan till [!UICONTROL CSP] header.

   Använd `generateNonce` function in `Magento\Csp\Helper\CspNonceProvider` för att få [!DNL nonce] sträng.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Lägg till en [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) till din moduls `csp_whitelist.xml` -fil.

## Problem - Betalningsmetoden saknas eller fungerar inte

Betalningsmetoden saknas eller fungerar inte med administratören **beställa skapa sida**, med &quot;*Avvisad körning av textbundet skript eftersom det bryter mot följande direktiv om säkerhetsprincip för innehåll: &quot;script-src ...*&quot; i webbläsarkonsolloggen.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Skapa en ny order.
1. Skapa en ny kund.
1. Ange kundinformationen.
1. Ange orderdetaljer (produkter, leveranssätt).
1. Välj en betalningsmetod.

<u>Förväntade resultat</u>:

Du kan välja en betalningsmetod och fortsätta att göra en beställning.

<u>Faktiska resultat</u>:

Betalningsmetoden saknas eller fungerar inte. Följande [!DNL JS] fel visas i webbläsarkonsolloggen: &quot;*Avvisad körning av textbundet skript eftersom det bryter mot följande direktiv om säkerhetsprincip för innehåll: &quot;script-src ...*&quot;.

### Orsak

I Adobe Commerce och Magento Open Source, version 2.4.7 och senare, **[!UICONTROL CSP]** är konfigurerad i `restrict-mode`, som standard, för betalningssidor i butiks- och administrationsområdet, och i `report-only` läge för alla andra sidor.
Motsvarande **[!UICONTROL CSP]** rubriken innehåller inte `unsafe-inline` nyckelord i `script-src` direktiv för betalningssidor. Dessutom, endast [!DNL whitelisted] textbundna skript tillåts.

### Lösning

Användare kan se webbläsarfel på grund av att vissa skript blockeras på grund av **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Du måste antingen</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de blockerade skripten med `SecureHtmlRenderer` klassen.
1. Använd `CSPNonceProvider` för att tillåta att skript körs.
Adobe Commerce och Magento Open Source 2.4.7 och senare innehåller en **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] leverantör för att underlätta generering av unika [!DNL nonce] strängar för varje begäran. Dessa [!DNL nonce] strängarna kopplas sedan till [!UICONTROL CSP] header.

   Använd `generateNonce` function in `Magento\Csp\Helper\CspNonceProvider` för att få [!DNL nonce] sträng.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [lägg till en [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) till din moduls `csp_whitelist.xml` -fil.

## Problem - Administratören kan inte göra en beställning

En administratör kan inte skicka in en beställning från administratören **skapa ordersida**, med &quot;*Avvisad körning av textbundet skript eftersom det bryter mot följande direktiv om säkerhetsprincip för innehåll: &quot;script-src ...*&quot; i webbläsarkonsolloggen.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Skapa en ny order.
1. Skapa en ny kund.
1. Ange kundinformationen.
1. Ange orderdetaljer (produkter, leveranssätt).
1. Välj en betalningsmetod.
1. Skicka ordern.

<u>Förväntade resultat</u>:

Du kan skicka en beställning.

<u>Faktiska resultat</u>:

Du kan inte skicka in en beställning. Följande [!DNL JS] fel visas i webbläsarkonsolloggen: &quot;*Avvisad körning av textbundet skript eftersom det bryter mot följande direktiv om säkerhetsprincip för innehåll: &quot;script-src ...*&quot;

### Orsak

I Adobe Commerce och Magento Open Source, version 2.4.7 och senare, **[!UICONTROL CSP]** är konfigurerad i `restrict-mode`, som standard, för betalningssidor i butiks- och administrationsområdet, och i `report-only` läge för alla andra sidor.
Motsvarande **[!UICONTROL CSP]** rubriken innehåller inte `unsafe-inline` nyckelord i `script-src` direktiv för betalningssidor. Dessutom, endast [!DNL whitelisted] textbundna skript tillåts.

### Lösning

Användare kan se webbläsarfel på grund av att vissa skript blockeras på grund av **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Du måste antingen</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de blockerade skripten med `SecureHtmlRenderer` klassen.
1. Använd `CSPNonceProvider` för att tillåta att skript körs.
Adobe Commerce och Magento Open Source 2.4.7 och senare innehåller en **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] leverantör för att underlätta generering av unika [!DNL nonce] strängar för varje begäran. Dessa [!DNL nonce] strängarna kopplas sedan till [!UICONTROL CSP] header.

   Använd `generateNonce` function in `Magento\Csp\Helper\CspNonceProvider` för att få [!DNL nonce] sträng.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Lägg till en [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) till din moduls `csp_whitelist.xml` -fil.
