---
title: Blockera skadlig trafik för Adobe Commerce på snabbnivå
description: I den här artikeln beskrivs de åtgärder du kan vidta för att blockera skadlig trafik när du misstänker att en DoS-attack inträffar i din Adobe Commerce på molninfrastrukturbutik.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# Blockera skadlig trafik för Adobe Commerce på snabbnivå

I den här artikeln beskrivs de åtgärder du kan vidta för att blockera skadlig trafik när du misstänker att en DoS-attack inträffar i din Adobe Commerce på molninfrastrukturbutik.

## Berörda produkter och versioner:

* Adobe Commerce i molninfrastruktur 2.3.x

I den här artikeln antar vi att du redan har de skadliga IP-adresserna och/eller deras land och användaragenter. Adobe Commerce i molninfrastruktur får vanligtvis den här informationen från Adobe Commerce support. I följande avsnitt beskrivs hur du blockerar trafik baserat på den här informationen. Alla ändringar ska göras i produktionsmiljön.

## Få åtkomst till administratörspanelen

Om webbplatsen är överbelastad av DoS kanske du inte kan logga in på din Commerce Admin (och utföra alla steg som beskrivs nedan).

Om du vill få åtkomst till Admin försätter du webbplatsen i underhållsläge enligt beskrivningen i [Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html#instgde-cli-maint) och vitlista din IP-adress. Inaktivera underhållsläget när detta är klart.

## Blockera trafik efter IP

För Adobe Commerce i molninfrastrukturbutiken är det mest effektiva sättet att blockera trafik med specifika IP-adresser och undernät att lägga till en ACL för Fast i Commerce Admin. Följ de här stegen med länkar till mer detaljerade anvisningar:

1. I Commerce Admin går du till **Lager** > **Konfiguration** > **Avancerat** > **System** > **Helsidescache** > **Snabb konfiguration**.
1. [Skapa en ny ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) med en lista över IP-adresser eller undernät som du ska blockera.
1. Lägg till den i ACL-listan och -blocket enligt beskrivningen i [Blockera](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) guide för modulen Fastly\_Cdn för Adobe Commerce.

## Blockera trafik per land

För Adobe Commerce i molninfrastrukturbutiken är det mest effektiva sättet att blockera trafik per land att lägga till en ACL för Fast i Commerce Admin.

1. I Commerce Admin går du till **Lager** > **Konfiguration** > **Avancerat** > **System** > **Helsidescache** > **Snabb konfiguration**.
1. Välj länder och konfigurera blockering med ACL enligt anvisningarna i [Blockera](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) guide för modulen Fastly\_Cdn för Adobe Commerce.

## Blockera trafik av användaragent

Om du vill skapa blockering baserat på användaragent måste du lägga till ett anpassat VCL-fragment i din snabbkonfiguration. Gör så här:

1. I Commerce Admin går du till **Lager** > **Konfiguration** > **Avancerat** > **System** > **Helsidescache**.
1. Sedan **Snabb konfiguration** > **Anpassade VCL-kodfragment**.
1. Skapa det nya anpassade fragmentet enligt beskrivningen i [Anpassade VCL-fragment](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) guide för modulen Fast\_Cdn. Du kan använda följande kodexempel som exempel. Det här exemplet tillåter inte trafik för `AhrefsBot` och `SemrushBot` användaragenter.

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot|SemrushBot)" ) {
      error 405 "Not allowed";
  }
```

## Hastighetsbegränsning (experimentell snabbfunktion)

Det finns en experimentell snabbfunktion för Adobe Commerce i molninfrastrukturen som gör att du kan ange hastighetsbegränsningen för vissa sökvägar och crawler. Se [Dokumentation för modulen Snabb](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md) för mer information.

Funktionaliteten måste testas utförligt på mellanlagring innan den används i produktionen eftersom den kan blockera legitim trafik.

## Rekommenderas: överväg att uppdatera robots.txt

Uppdatera din `robots.txt` kan hjälpa till att förhindra att vissa sökmotorer, crawlningar och robotar crawlar vissa sidor. Exempel på sidor som inte ska crawlas är sökresultatsidor, utcheckning, kundinformation och så vidare. Att förhindra robotar från att crawla dessa sidor kan bidra till att minska antalet begäranden som genereras av dessa robotar.

Det finns två viktiga saker att tänka på när du använder `robots.txt`:

* Robotar kan ignorera `robots.txt`. I synnerhet robotar för skadlig kod som skannar webben efter säkerhetsproblem och e-postadresskörare som används av spamrerare kommer inte att bry sig.
* The `robots.txt` filen är en offentligt tillgänglig fil. Vem som helst kan se vilka delar av servern som du inte vill att robotar ska använda.

Grundläggande information och Adobe Commerce som standard `robots.txt` finns i [Sökmotorrobotar](https://docs.magento.com/m2/ee/user_guide/marketing/search-engine-robots.html) artikel i vår dokumentation för utvecklare.

Allmän information och rekommendationer om `robots.txt`, se:

* [Skapa en robot.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) fil från Google Support
* [Om /robots.txt](https://www.robotstxt.org/robotstxt.html) av robotstxt.org

Arbeta med utvecklaren och/eller SEO-experten för att avgöra vilka användaragenter du vill tillåta eller vilka du vill neka.

## Relaterad läsning

[Produktspecifika licensieringsvillkor för Adobe Commerce i molnet](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
