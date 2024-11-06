---
title: Adobe Commerce snabbfelsökare
description: Den här snabbfelsökaren för Adobe Commerce-användare vägleder dig till lösningar baserat på ditt svar på de symtom du ser. Klicka på frågorna för att se nästa alternativ eller svar.
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Adobe Commerce snabbfelsökare

Den här snabbfelsökaren för Adobe Commerce-användare vägleder dig till lösningar baserat på ditt svar på de symtom du ser. Klicka på frågorna för att se nästa alternativ eller svar.

## Steg 1 - Bekräfta snabb service {#step-1}

+++**Kunden rapporterar ett problem med Fastly. Är snabbtjänsten avstängd?**

a. JA - Kontrollera [Snabb servicestatus](https://status.fastly.com/) och [skicka en Adobe Commerce-supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEJ - Fortsätt till [steg 2](#step-2).

+++

## Steg 2 - Kontrollera VCL-konfigurationsfilen {#step-2}

+++**Har du några fel när du kör backend Tester?**

Kör ditt projekt-URL via [backend Tester - snabbt](https://magento-tester.global.ssl.fastly.net/magento-tester/). Den visar versionen av VCL-konfigurationsfilen, om sidan är tillgänglig, versionen av modulen Snabbt och annan användbar felsökningsinformation. Har du några fel?

a. JA - Meddelandet _Plugin VCL-versionen är inaktuell! Ladda upp igen._ Information om lösningen på det här felet finns i [Snabbt fel: Plugin VCL-versionen är inaktuell! Ladda upp](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md) igen.\
b. NEJ - [Steg 3](#step-3).

+++

## Steg 3 - Kontrollera om det finns något fel med bildoptimering {#step-3}

+++**Bildoptimeringsfel?**

a. JA - [Fel vid aktivering av bildoptimering](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md).\
b. NO - Kontrollera DNS genom att köra i CLI/terminal: `dig [your website.com] + short`. Fortsätt till [Steg 4](#step-4).

+++

## Steg 4 - Verifiera DNS {#step-4}

+++**Vad händer när du kör `dig`?**

När du körde `dig` returnerade det en post som pekar på prod.magentocloud.map.fastly.net eller någon av följande IP-adresser (se [Uppdatera DNS-konfiguration med produktionsinställning](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings) i utvecklardokumentationen):

* 151.101.1.124
* 151.101.65.124
* 151.101.129.124
* 151.101.193.124

a. JA - Problemet är inte DNS-relaterat. Fortsätt till [Steg 5](#step-5).\
b. NEJ - Problemet är sannolikt DNS-relaterat. Kunden bör [kontrollera DNS-konfigurationen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings) eller kontakta sin DNS-leverantör för mer information.

+++

## Steg 5 - Bekräfta anslutning {#step-5}

+++**Får du ett meddelande om att anslutningen är osäker eller inte säker när du kör `curl -svo /dev/null "https://website.com"` i CLI/Terminal?**

a. JA - Detta är troligen ett certifikatproblem. Besök webbplatsen i en webbläsare och välj låsikonen och leta efter certifikatets förfallodatum. Fortsätt till [Steg 6](#step-6).\
b. NEJ - Besök [http://fastly-debug.com](https://www.fastly-debug.com/) och dela den här informationen i en [Adobe Commerce supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 6 - Bekräfta att du har ett giltigt TSL-certifikat {#step-6}

+++**Har certifikatet gått ut?**

a. JA - Du måste förnya ditt TLS-certifikat med certifikatutfärdaren.\
b. NEJ - Du kanske inte har något certifikat alls. Om du har Adobe Commerce rekommenderar vi att du köper ett TLS-certifikat. Om du använder Adobe Commerce i en molninfrastruktur kan du ha ett domänvaliderat Låt oss kryptera SSL-/TLS-certifikat för säker HTTPS-trafik från Fast. Se [etablera SSL-/TLS-certifikat](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) i utvecklardokumentationen.

+++

[Tillbaka till steg 1](#step-1)
