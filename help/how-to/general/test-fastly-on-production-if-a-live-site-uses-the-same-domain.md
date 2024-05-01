---
title: Testa snabbt i produktionen om en Live Site använder samma domän
description: Om du har en aktiv webbplats som är igång i din produktionsdomän (`example.com`) och du behöver testa din nya butik på Adobe Commerce i molninfrastrukturens produktionsmiljö med Fastly CDN aktiverat, rekommenderar vi att du använder underdomänen (som "prod.example.com"), som tidigare har lagt till den i Fastly, för alla testaktiviteter före start. I den här artikeln beskrivs detaljerna och här finns användbara länkar till Adobe Commerce dokumentationsresurser.
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Testa snabbt i produktionen om en Live Site använder samma domän

Om du har en aktiv webbplats som körs på din produktionsdomän (`example.com`) och du behöver testa din nya butik på Adobe Commerce i molninfrastrukturens produktionsmiljö med Fast CDN aktiverat, rekommenderar vi att du använder underdomänen (som `prod.example.com`), som tidigare lagt till den i Fastly, för alla testaktiviteter före lanseringen. I den här artikeln beskrivs detaljerna och här finns användbara länkar till Adobe Commerce dokumentationsresurser.

## Problem

Din aktuella butik som använder `example.com` produktionsdomänen är aktiv och fungerar. Du måste emellertid testa din nya butik, som byggts med Adobe Commerce i molninfrastruktur och distribuerats i produktionsmiljön, med tjänsten Fast full page cache aktiverad.

Problemet är att produktionsmiljön i ditt Adobe Commerce i molninfrastrukturprojekt använder samma aktiva domän (`example.com`) och du kan inte växla din nya webbplats till den här domänen samtidigt som din aktuella livebutik körs - på samma domän.

### Varför ska man använda Snabbt för testning i produktionsmiljön?

Teoretiskt sett kan du hoppa över att använda Fast CDN och testa Adobe Commerce i molninfrastrukturbutiken i produktionsmiljön utan att helsidescachen är aktiverad.

Men om helsidescachen är aktiverad fungerar din butik annorlunda. Du kan aldrig känna till webbplatsens verkliga liveprestanda om du inte har testat den med CDN innan du startar den. Den officiella Adobe Commerce-rekommendationen är att testa din butik i produktion med Fast CDN aktiverat.

## Lösning: använd produktionsunderdomän

Använd den första underdomänen (`prod.example.com`) för din nya Adobe Commerce i molninfrastrukturbutiken i produktionsmiljön samtidigt som den aktuella livewebbplatsen finns i basdomänen (`example.com`).

När du planerar ditt Adobe Commerce-projekt för molninfrastruktur kan du ange en sådan underdomän och begära att molninfrastruktursteamet pekar underdomänen mot tjänsten Fast.

Följ de här stegen för att bearbeta underdomänen i ditt Adobe Commerce i ett molninfrastrukturprojekt:

* [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) begär att underdomänen ska läggas till i Snabb-tjänsten/Nginx-konfigurationen (för Adobe Commerce i Cloud Infrastructure Pro-planarkitekturen).
* Konfigurera motsvarande DNS-inställningar.

När du har utfört stegen för konfiguration av underdomäner måste du också göra följande för att validera din produktionsdomän för SSL-certifikatet:

* Överför DNS TXT-posten för SSL-validering av produktionsdomänen.
* [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) begär att få validera produktionsdomänen för SSL-certifikatet.

Om du använder underdomänen kan du göra en &quot;mjuk start&quot; av din butik i framtiden, eftersom en sådan start bara kräver att motsvarande DNS-inställningar uppdateras.

## Relaterad dokumentation

I vår kunskapsbas:

* [Konfigurera snabbt DNS-inställningar i mellanlagrings- och produktionsmiljöer](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html)
* [Konfigurera Fast för Starter-planen i molnet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html)
* [Potentiella blockerare för lansering på Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html)

I vår utvecklardokumentation:

* [Snabb översikt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Go live checklist: DNS configurations for Fast](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html)
