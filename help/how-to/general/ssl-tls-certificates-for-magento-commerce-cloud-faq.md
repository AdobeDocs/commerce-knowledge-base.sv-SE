---
title: SSL-certifikat (TLS) för Adobe Commerce i molninfrastruktur
description: I den här artikeln finns snabba svar på frågor om hur du får SSL-certifikat (TLS) för din Adobe Commerce-webbplats i vår molninfrastruktur.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 7694e6cb739d73a28c902e95d324b1317f4daaf6
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# SSL-certifikat (TLS) för Adobe Commerce i molninfrastruktur

I den här artikeln finns snabba svar på frågor om hur du får SSL-certifikat (TLS) för din Adobe Commerce-webbplats i vår molninfrastruktur.

## Vilket SSL/TLS-certifikat tillhandahåller Adobe?

Adobe tillhandahåller ett domänverifierat [Låt oss kryptera SSL-/TLS-certifikat](https://letsencrypt.org/) för att tillhandahålla säker HTTPS-trafik från [!DNL Fastly]. Adobe tillhandahåller ett certifikat för varje Adobe Commerce för molninfrastruktur Pro-planens arkitektur, mellanlagring och Adobe Commerce för arkitekturmiljön Starter för molninfrastruktur för att skydda alla domäner i den miljön.

## Vad omfattar ett certifikat?

För Pro-planarkitekturen skapas ett SSL-certifikat för både miljöer för mellanlagring och produktion. Varje dedikerad miljö som ligger utanför Apple Platform-as-a-Service-integreringsmiljön (PaaS) kommer att ha det här certifikatet för de URL:er som är tilldelade till den miljön.

För startplanens arkitektur och PaaS-integreringsmiljöer finns det en standardteknisk domän som tillhandahålls med miljön och skyddas av ett separat certifikat.

## Hur lägger jag till en ny domän för det befintliga certifikatet?

Så här lägger du till domänen till tjänsten i [!DNL Fastly]:

1. Peka din domän i DNS på prod.magentocloud.map.fastly.net och vänta i upp till 6 timmar.
1. [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) som begär att få lägga till den här domänen i Nginx-konfigurationen (om du inte har gjort det tidigare).

## Hur begär jag ett certifikat?

Fall 1

Om du inte har startat någon webbplats ännu kan du ha fått ACME Challenge CNAME från din kundtekniska rådgivare (CTA). Du behöver bara ha en ACME-utmaning om du inte omedelbart kan peka din DNS mot din produktions-URL och behöver få SSL-certifikaten skapade i förväg.

Fall 2

Om din webbplats redan är aktiv och/eller du kan peka URL:er som ska användas för din aktiva webbplats direkt, behöver du inte begära en ACME CNAME. När du har lagt till URL:er till din Adobe Commerce på molninfrastrukturwebbplats och pekar din DNS på [!DNL Fastly], fungerar HTTP-verifieringen och skapar antingen ditt SSL-certifikat för första gången eller uppdaterar certifikatet med ytterligare URL:er.

## Kan jag använda mitt eget SSL-/TLS-certifikat?

Du kan ange ett eget SSL-/TLS-certifikat i stället för att använda [Låt oss kryptera certifikatet](https://letsencrypt.org/) som tillhandahålls av Adobe.

Den här processen kräver dock ytterligare arbete för att kunna konfigurera och underhålla. Du måste först generera en CSR (Certificate Signing Request) för webbplatsens domännamn (eller vanliga namn) och ange den till din SSL-leverantör för att kunna tillhandahålla ett SSL-certifikat.

När du har SSL-certifikatet skickar du en [Adobe Commerce-supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) eller arbetar med din CTA för att lägga till anpassade värdcertifikat i dina molnmiljöer.

* Om domänerna inte längre används rensas de automatiskt från vårt system och inga ytterligare åtgärder krävs.
* Om du redan äger ett certifikat kan du överföra det med en SFTP-klient (SSH File Transfer Protocol) till en plats på servern som inte är tillgänglig på webben och [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) som meddelar filsökvägen.

>[!WARNING]
>
>Det är viktigt att du inte överför certifikatfilerna direkt till biljetten. Annars betraktas certifikaten som komprometterade och Adobe måste begära ett nytt certifikat.
>Filerna ska överföras via SFTP till servern i en mapp som du väljer, t.ex. `var/ssl`, `/tmp/ssl` osv. - använd inga andra metoder som att implementera filerna i databasen (vilket endast bör göras för oföränderliga filer som inte innehåller känsliga data).

## Certifikatets namn

Namnet på SSL-certifikatet gäller bara för den primära URL:en, och det är det primära värdnamnet som namnges av den första URL:en och måste matcha för att kunna valideras och skapas. Om du har ett fåtal URL-adresser läggs de till som alternativa ämnesnamnposter i certifikatet. Om du har flera URL:er som pekar mot en Adobe Commerce på en molninfrastrukturwebbplats har du bara ett gemensamt namn-URL-certifikat som sedan har alternativa ämnesnamn som skyddar webbplatsen med SSL.

## Vilken domän visas i fältet Gemensamt namn för certifikatet?

Domänen som visas på certifikatet är bara den första domänen som läggs till i TLS-certifikatet, fyller i fältet **Gemensamt namn** (**CN**) och webbläsarna visar det här namnet först. Fältet **Alternativt ämnesnamn** (**SAN**) innehåller alla DNS-namn för TLS-certifikatet. Det finns inget sätt att ändra eller begära det gemensamma namnet som visas.

## Kan jag använda TLS-certifikat med jokertecken?

TLS-certifikat med jokertecken kan bara användas med ditt anpassade certifikat och inte med Adobe Commerce Let&#39;s Encrypt-certifikat. Som en del av vår TLS-optimering upphör Adobe med stödet för TLS-jokertecken. Vi identifierar och kontaktar handlare som använder ett jokertecken med Adobe Let&#39;s Encrypt-certifikat och som har konfigurerats i [!DNL Fastly]-konsolen för Adobe Commerce. Vi ber att dessa jokertecken ersätts med exakta domäner för att säkerställa TLS-täckning. Om du vill ersätta ett TLS-certifikat med jokertecken går du till [domänavsnittet](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration#manage-domains) i plugin-programmet [!DNL Fastly]. Här kan du lägga till exakta domäner och ta bort jokertecknet. Observera att DNS måste peka på [!DNL Fastly] för dessa nya domäner för att kunna dirigera via CDN. När domänerna har lagts till och DNS har uppdaterats kommer ett matchande [Låt oss kryptera](https://letsencrypt.org/)-certifikat att etableras. Om du inte tar bort en domän som pekar på [!DNL Fastly] med hjälp av ett jokertecken kommer Adobe att ta bort det delade certifikatet. Detta kan leda till ett webbplatsutbrott om du inte har konfigurerat URL:ens FQDN och samma URL FQDN konfigurerad i din DNS. Du bör därför bekräfta att de konfigurerade URL:erna också har en-till-en-matchning i sin DNS som pekar på [!DNL Fastly].

## Vad ska jag göra om min domän inte längre pekar på Adobe Commerce?

Om din domän inte längre pekar på Adobe Commerce tar du bort den från [!DNL Fastly]/Adobe Commerce-systemet. Mer information finns i [!DNL Fastly] [Ta bort en domän](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain). Du behöver inte peka din domän mot Adobe Commerce, men du måste kontrollera om det krävs ett TLS-certifikat för den högsta domänen. Om en domän på den högsta nivån krävs måste du uppdatera din DNS så att den pekar på Adobe Commerce. Om den redan pekar på Adobe Commerce ska du uppdatera CAA-posten så att den innehåller [lets-encrypt](https://letsencrypt.org/). Om du utför de här stegen visas LE Cert uppdaterad med de sekundära URL:er som certifikatet täcker. &#x200B;

## Relaterad läsning

[Tillhandahåller SSL-/TLS-certifikat](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) i utvecklardokumentationen
