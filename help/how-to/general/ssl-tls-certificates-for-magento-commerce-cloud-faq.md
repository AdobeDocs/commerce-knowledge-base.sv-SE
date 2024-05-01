---
title: SSL-certifikat (TLS) för Adobe Commerce i molninfrastruktur
description: I den här artikeln finns snabba svar på frågor om hur du får SSL-certifikat (TLS) för din Adobe Commerce-webbplats i vår molninfrastruktur.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 43c3e5f95c4b54e235140cd5b3978d3887af5ee1
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# SSL-certifikat (TLS) för Adobe Commerce i molninfrastruktur

I den här artikeln finns snabba svar på frågor om hur du får SSL-certifikat (TLS) för din Adobe Commerce-webbplats i vår molninfrastruktur.

## Vilket SSL/TLS-certifikat tillhandahåller Adobe?

Adobe tillhandahåller en domänverifierad [Låt oss kryptera SSL-/TLS-certifikat](https://letsencrypt.org/) för säker HTTPS-trafik från [!DNL Fastly]. Adobe tillhandahåller ett certifikat för varje Adobe Commerce för molninfrastruktur Pro-planens arkitektur, mellanlagring och Adobe Commerce för arkitekturmiljön för Starter-planer i molninfrastrukturen för att skydda alla domäner i den miljön.

## Vad omfattar ett certifikat?

För Pro-planarkitekturen skapas ett SSL-certifikat för både miljöer för mellanlagring och produktion. Varje dedikerad miljö som ligger utanför Apple Platform-as-a-Service-integreringsmiljön (PaaS) kommer att ha det här certifikatet för de URL:er som är tilldelade till den miljön.

För startplanens arkitektur och PaaS-integreringsmiljöer finns det en standardteknisk domän som tillhandahålls med miljön och skyddas av ett separat certifikat.

## Hur lägger jag till en ny domän för det befintliga certifikatet?

Lägga till domänen i tjänsten i [!DNL Fastly]:

1. Peka din domän i DNS på prod.magentocloud.map.fastly.net och vänta i upp till 6 timmar.
1. [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) begär att få lägga till den här domänen i Nginx-konfigurationen (om du inte har gjort det tidigare).

## Hur begär jag ett certifikat?

Fall 1

Om du inte har startat någon webbplats ännu kan du ha fått ACME Challenge CNAME från din kundtekniska rådgivare (CTA). Du behöver bara ha en ACME-utmaning om du inte omedelbart kan peka din DNS mot din produktions-URL och behöver få SSL-certifikaten skapade i förväg.

Fall 2

Om din webbplats redan är aktiv och/eller du kan peka URL:er som ska användas för din aktiva webbplats direkt, behöver du inte begära en ACME CNAME. När du har lagt till de URL:er som behövs på din Adobe Commerce-webbplats för molninfrastruktur och pekar din DNS på [!DNL Fastly]fungerar HTTP-verifieringen och skapar antingen SSL-certifikatet för första gången eller uppdaterar certifikatet med ytterligare URL:er.

## Kan jag använda mitt eget SSL-/TLS-certifikat?

Du kan ange ett eget SSL-/TLS-certifikat i stället för att använda [Låt oss kryptera certifikatet](https://letsencrypt.org/) tillhandahålls av Adobe.

Den här processen kräver dock ytterligare arbete för att kunna konfigurera och underhålla. Du måste först generera en CSR (Certificate Signing Request) för webbplatsens domännamn (eller vanliga namn) och ange den till din SSL-leverantör för att kunna tillhandahålla ett SSL-certifikat.

När du har ett SSL-certifikat skickar du en [Adobe Commerce Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) eller arbeta med din CTA för att lägga till anpassade certifikat i dina molnmiljöer.

* Om domänerna inte längre används rensas de automatiskt från vårt system och inga ytterligare åtgärder krävs.
* Om du redan äger ett certifikat kan du överföra det med en SFTP-klient (SSH File Transfer Protocol) till en plats på servern som inte är tillgänglig på webben. [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) meddela dem filens sökväg.

>[!WARNING]
>
>Det är viktigt att du inte överför certifikatfilerna direkt till biljetten. I annat fall betraktas certifikaten som komprometterade och Adobe måste begära ett nytt certifikat.
>Filerna ska överföras via SFTP till servern - använd inga andra metoder som att implementera filerna i databasen (vilket bara ska göras för oföränderliga filer som inte innehåller känsliga data).

## Certifikatets namn

Namnet på SSL-certifikatet gäller bara för den primära URL:en, och det är det primära värdnamnet som namnges av den första URL:en och måste matcha för att kunna valideras och skapas. Om du har ett fåtal URL-adresser läggs de till som alternativa ämnesnamnposter i certifikatet. Om du har flera URL:er som pekar mot en Adobe Commerce på en molninfrastrukturwebbplats har du bara ett gemensamt namn-URL-certifikat som sedan har alternativa ämnesnamn som skyddar webbplatsen med SSL.

## Vilken domän visas i fältet Gemensamt namn för certifikatet?

Domänen som visas på certifikatet är bara den första domänen som läggs till i TLS-certifikatet, den fyller i **Namn** (**CN**) och webbläsarna visar det här namnet först. The **Alternativt namn på ämne** (**SAN**) innehåller alla DNS-namn för TLS-certifikatet. Det finns inget sätt att ändra eller begära det gemensamma namnet som visas.

## Kan jag använda TLS-certifikat med jokertecken?

TLS-certifikat med jokertecken kan bara användas med ditt anpassade certifikat och inte med Adobe Commerce Let&#39;s Encrypt-certifikat. Som en del av vår TLS-optimering upphör Adobe stödet för TLS-certifikat med jokertecken. Vi identifierar och kontaktar handlare som använder ett jokertecken med Adobe krypteringscertifikat och som är konfigurerade i [!DNL Fastly] Adobe Commerce. Vi ber att dessa jokertecken ersätts med exakta domäner för att säkerställa TLS-täckning. Om du vill ersätta ett TLS-jokertecken går du till [domänavsnitt](https://devdocs.magento.com/cloud/cdn/configure-fastly-customize-cache.html#manage-domains) i [!DNL Fastly] plugin-program. Här kan du lägga till exakta domäner och ta bort jokertecknet. Observera att DNS måste peka på [!DNL Fastly] för dessa nya domäner att dirigera genom CDN. När domänerna har lagts till och DNS har uppdaterats, matchar [Låt oss kryptera](https://letsencrypt.org/) certifikat kommer att etableras. Om du inte tar bort en domän som pekar på [!DNL Fastly] om du använder ett jokertecken tar Adobe bort det delade certifikatet. Detta kan leda till ett webbplatsutbrott om du inte har konfigurerat URL:ens FQDN och samma URL FQDN konfigurerad i din DNS. Du bör därför bekräfta att de konfigurerade URL-adresserna också har en-till-en-matchning i sina DNS-referenser som pekar på [!DNL Fastly].

## Vad ska jag göra om min domän inte längre pekar på Adobe Commerce?

Om din domän inte längre pekar på Adobe Commerce ska du ta bort den från [!DNL Fastly]/Adobe Commerce. Se [!DNL Fastly] [Ta bort en domän](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) om du vill veta mer. Du behöver inte peka din domän mot Adobe Commerce, men du måste kontrollera om det krävs ett TLS-certifikat för den högsta domänen. Om en domän på den högsta nivån krävs måste du uppdatera din DNS så att den pekar på Adobe Commerce. Om det redan pekar på Adobe Commerce ska du uppdatera CAA-posten till att inkludera [lets-encrypt](https://letsencrypt.org/). Om du utför de här stegen visas LE Cert uppdaterad med de sekundära URL:er som certifikatet täcker. &#x200B;

## Relaterad läsning

[Tillhandahåll SSL-/TLS-certifikat](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates) i vår utvecklardokumentation
