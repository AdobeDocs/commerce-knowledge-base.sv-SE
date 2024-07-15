---
title: Omdirigera HTTP till HTTPS för alla sidor på Adobe Commerce om molninfrastruktur (Force TLS)
description: Aktivera Fast-funktionaliteten **Force TLS** i Commerce Admin för att aktivera den globala omdirigeringen av HTTP till HTTPS för alla sidor i Adobe Commerce i molninfrastrukturbutiken.
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Omdirigera HTTP till HTTPS för alla sidor på Adobe Commerce om molninfrastruktur (Force TLS)

Aktivera snabbhetens **Tvinga TLS**-funktion i Commerce Admin för att aktivera den globala omdirigeringen från HTTP till HTTPS för alla sidor i din Adobe Commerce i molninfrastrukturbutiken.

Den här artikeln innehåller detaljerade [steg](#steps), en snabb översikt av Tvinga TLS-funktionen, berörda versioner och länkar till relaterad dokumentation.

## Steg {#steps}

### Steg 1: Konfigurera säkra URL:er {#step-1-configure-secure-urls}

I det här steget definierar vi säkra URL:er för butiken. Gå till [Steg 2: Aktivera Tvinga TLS](#step-2-enable-force-tls) om det redan är klart.

1. Logga in på Commerce Admin.
1. Navigera till **Lagrar** > **Konfiguration** > **Allmänt** > **Webb**.
1. Expandera avsnittet **Bas-URL:er (säkra)**.    ![magento-admin_base-urls-secure.png](assets/magento-admin_base-urls-secure.png)
1. Ange HTTPS-URL:en för din butik i fältet **Säker bas-URL**.
1. Ange **Använd säkra URL:er i Storefront** och **Använd säkra URL:er i Admin**-inställningarna till **Ja**.    ![magento-admin_base-urls-secure-settings.png](assets/magento-admin_base-urls-secure-settings.png)
1. Klicka på **Spara konfig** i det övre högra hörnet om du vill använda ändringarna.

**Relaterad dokumentation i vår användarhandbok:**   [Lagra URL:er](https://docs.magento.com/m2/ee/user_guide/stores/store-urls.html).

### Steg 2: Aktivera Tvinga TLS {#step-2-enable-force-tls}

1. Gå till **Lagrar** > **Konfiguration** > **Avancerat** > **System** i Commerce Admin.
1. Expandera avsnittet **Helsidescache**, **Snabbkonfiguration** och sedan **Avancerad konfiguration**.
1. Klicka på knappen **Tvinga TLS**.    ![magento-admin_force-tls-button.png](assets/magento-admin_force-tls-button.png)
1. Klicka på **Överför** i den dialogruta som visas.    ![magento-admin_force-tls-confirmation-dialog.png](assets/magento-admin_force-tls-confirmation-dialog.png)
1. När dialogrutan stängs kontrollerar du att det aktuella läget för Tvinga TLS visas som **aktiverat**.    ![magento-admin_force-tls-enabled.png](assets/magento-admin_force-tls-enabled.png)

**Snabbt relaterad dokumentation:**   [ Tvinga TLS-guide ](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md) för Adobe Commerce 2.

## Om Tvinga TLS

TLS (Transport Layer Security) är ett protokoll för säkra HTTP-anslutningar som ersätter den mindre säkra föregångaren, SSL-protokollet (Secure Socket Layer).

Med Fast&#39;s Force TLS-funktionen kan du tvinga alla inkommande okrypterade förfrågningar för dina webbplatssidor till TLS.

>>
Det fungerar genom att returnera ett *301 Flyttat permanent* -svar på en okrypterad begäran, som dirigeras om till TLS-motsvarigheten. Om du till exempel gör en begäran för *http://www.example.com/foo.jpeg* dirigeras den om till *https://www.example.com/foo.jpeg*.

[Skydda kommunikationen](https://docs.fastly.com/guides/securing-communications/) (snabb dokumentation)

## Berörda versioner

* **Adobe Commerce i molninfrastruktur:**
   * version: 2.1.4 och senare
   * planer: Adobe Commerce om molninfrastruktur Starter-planarkitektur och Adobe Commerce om molninfrastruktur Pro-planarkitektur (inklusive Pro Legacy)
* **Snabbt:** 1.2.4

## Inga ändringar behövs för vägar.yaml

Om du vill aktivera omdirigering från HTTP till HTTPS på **alla** sidor i din butik behöver du inte lägga till sidorna i `routes.yaml`-konfigurationsfilen. Det räcker att aktivera Tvinga TLS globalt för hela butiken (med Commerce Admin).

## Dokumentation som hänger ihop snabbt

* [Tvinga TLS-guide för Adobe Commerce 2](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [Framtvingar en TLS-omdirigering](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect)
* [Skyddar kommunikation](https://docs.fastly.com/guides/securing-communications/)
