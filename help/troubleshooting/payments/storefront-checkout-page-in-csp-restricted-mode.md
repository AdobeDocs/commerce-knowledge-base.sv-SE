---
title: Felsöka utcheckningssidan för butiker i [!UICONTROL CSP] begränsat läge
description: I den här artikeln förklaras de fel som kan uppstå när du visar utcheckningssidan i begränsat CSP-läge, och här finns lösningar på felen.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Felsöka utcheckningssidan för butiker i [!UICONTROL CSP] begränsat läge

I den här artikeln ges förklaringar och korrigeringar för Adobe Commerce 2.4.7-problem när du visar utcheckningssidan i **[!UICONTROL CSP restricted mode]**, med felmeddelandet *Nekas att köra infogat skript eftersom det bryter mot följande direktiv för innehållssäkerhetsprincip: &quot;script-src ...*&quot; i webbläsarkonsolloggen.

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur, Adobe Commerce lokalt och Magento Open Source:

* 2.4.7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Problem - Utcheckningssidan för Storefront är skadad eller kan inte läsas in

Sidan **storefront checkout** är trasig eller kan inte läsas in, med felmeddelandet *Nekad körning av infogat skript eftersom den bryter mot följande direktiv för innehållssäkerhetsprincip: &quot;script-src ...*&quot; i webbläsarkonsolloggen.

<u>Steg som ska återskapas</u>:

1. Gå till butiken.
1. Lägg en produkt i kundvagnen och fortsätt till kassan.

<u>Förväntade resultat</u>:

Utcheckningssidan läses in helt normalt.

<u>Faktiska resultat</u>:

Utcheckningssidan är tom eller saknar komponenter. Följande [!DNL JS]-fel visas i webbläsarens konsollogg: *Avvisad att det infogade skriptet inte kan köras eftersom det bryter mot följande direktiv för säkerhetsprincip för innehåll: &quot;script-src ...*&quot;

### Orsak

I Adobe Commerce och Magento Open Source, version 2.4.7 och senare, är **[!UICONTROL CSP]** som standard konfigurerat i `restrict-mode` för betalningssidor i butiks- och administratörsområdet och i `report-only`-läge för alla andra sidor.
Motsvarande **[!UICONTROL CSP]**-rubrik innehåller inte nyckelordet `unsafe-inline` i direktivet `script-src` för betalningssidor. Dessutom tillåts bara [!DNL whitelisted] textbundna skript.

### Lösning

Användare kan se webbläsarfel på grund av att vissa skript blockeras på grund av **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Du måste antingen</u> för att kunna åtgärda problemet:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) blockerade skript med klassen `SecureHtmlRenderer`.
1. Använd klassen `CSPNonceProvider` om du vill tillåta att skript körs.
Adobe Commerce och Magento Open Source 2.4.7 och senare innehåller en **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce]-provider som gör det enklare att skapa unika [!DNL nonce] -strängar för varje begäran. Dessa [!DNL nonce] strängar kopplas sedan till rubriken [!UICONTROL CSP].

   Använd funktionen `generateNonce` i `Magento\Csp\Helper\CspNonceProvider` för att hämta en [!DNL nonce]-sträng.

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

1. [Lägg till en [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) i modulens `csp_whitelist.xml`-fil.

## Problem - Betalningsmetoden saknas eller fungerar inte

Betalningsmetoden saknas eller fungerar inte på **storefront-utcheckningssidan**, med *Refused to execute inline script eftersom den bryter mot följande direktiv för innehållets säkerhetsprincip: &quot;script-src ...*&quot; error message in the browser console log.

<u>Steg som ska återskapas</u>:

1. Gå till butiken.
2. Lägg en produkt i kundvagnen och fortsätt till kassan.
3. Välj en betalningsmetod.

<u>Förväntade resultat</u>:

Du kan välja en betalningsmetod och fortsätta att göra en beställning.

<u>Faktiska resultat</u>:

Betalningsmetoden saknas eller fungerar inte. Följande [!DNL JS]-fel visas i webbläsarens konsollogg: *Avvisad att det infogade skriptet inte kan köras eftersom det bryter mot följande direktiv för säkerhetsprincip för innehåll: &quot;script-src ...*&quot;

### Orsak

I Adobe Commerce och Magento Open Source, version 2.4.7 och senare, är **[!UICONTROL CSP]** som standard konfigurerat i `restrict-mode` för betalningssidor i butiks- och administratörsområdet och i `report-only`-läge för alla andra sidor.
Motsvarande **[!UICONTROL CSP]**-rubrik innehåller inte nyckelordet `unsafe-inline` i direktivet `script-src` för betalningssidor. Dessutom tillåts bara [!DNL whitelisted] textbundna skript.

### Lösning

Användare kan se webbläsarfel på grund av att vissa skript blockeras på grund av **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Du måste antingen</u> för att kunna åtgärda problemet:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) blockerade skript med klassen `SecureHtmlRenderer`.
1. Använd klassen `CSPNonceProvider` om du vill tillåta att skript körs.
Adobe Commerce och Magento Open Source 2.4.7 och senare innehåller en **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce]-provider som gör det enklare att skapa unika [!DNL nonce] -strängar för varje begäran. Dessa [!DNL nonce] strängar kopplas sedan till rubriken [!UICONTROL CSP].

   Använd funktionen `generateNonce` i `Magento\Csp\Helper\CspNonceProvider` för att hämta en [!DNL nonce]-sträng.

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

1. [Lägg till en [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) i modulens `csp_whitelist.xml`-fil.

## Problem - Kunden kan inte göra en beställning

En kund kan inte göra en beställning med felmeddelandet *Avvisad att köra ett textbundet skript eftersom det bryter mot följande direktiv om innehållets säkerhetsprincip: &quot;script-src ...*&quot; i webbläsarkonsolloggen.

<u>Steg som ska återskapas</u>:

1. Gå till butiken.
2. Lägg en produkt i kundvagnen och fortsätt till kassan.
3. Välj en betalningsmetod.
4. Klicka på **Montera order**.

<u>Förväntade resultat</u>:

Du kan göra en beställning.

<u>Faktiska resultat</u>:

Du kan inte göra en beställning. Följande [!DNL JS]-fel visas i webbläsarens konsollogg: *Avvisad att det infogade skriptet inte kan köras eftersom det bryter mot följande direktiv för säkerhetsprincip för innehåll: &quot;script-src ...*&quot;

### Orsak

I Adobe Commerce och Magento Open Source, version 2.4.7 och senare, är **[!UICONTROL CSP]** som standard konfigurerat i `restrict-mode` för betalningssidor i butiks- och administratörsområdet och i `report-only`-läge för alla andra sidor.
Motsvarande **[!UICONTROL CSP]**-rubrik innehåller inte nyckelordet `unsafe-inline` i direktivet `script-src` för betalningssidor. Dessutom tillåts bara [!DNL whitelisted] textbundna skript.

### Lösning

Användare kan se webbläsarfel på grund av att vissa skript blockeras på grund av **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Du måste antingen</u> för att kunna åtgärda problemet:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) blockerade skript med klassen `SecureHtmlRenderer`.
1. Använd klassen `CSPNonceProvider` om du vill tillåta att skript körs.
Adobe Commerce och Magento Open Source 2.4.7 och senare innehåller en **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce]-provider som gör det enklare att skapa unika [!DNL nonce] -strängar för varje begäran. Dessa [!DNL nonce] strängar kopplas sedan till rubriken [!UICONTROL CSP].

   Använd funktionen `generateNonce` i `Magento\Csp\Helper\CspNonceProvider` för att hämta en [!DNL nonce]-sträng.

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

1. [Lägg till en [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) i modulens `csp_whitelist.xml`-fil.
