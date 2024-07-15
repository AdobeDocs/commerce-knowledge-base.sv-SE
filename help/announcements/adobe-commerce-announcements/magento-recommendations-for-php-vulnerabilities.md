---
title: Sårbarheter i Adobe Commerce Recommendations for PHP
description: Den 3 september utfärdade MS-ISAC (Multi-State Information Sharing and Analysis Center) ett varningsmeddelande om flera säkerhetsluckor som skulle kunna möjliggöra exekvering av godtycklig kod och en rekommendation om att alla webbplatser som använder PHP ska uppdatera till den senaste PHP-versionen av ASAP ([fullständig varning finns här](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Sårbarheter i Adobe Commerce Recommendations for PHP

Den 3 september utfärdade MS-ISAC (Multi-State Information Sharing and Analysis Center) ett varningsmeddelande om flera säkerhetsluckor som skulle kunna möjliggöra godtycklig exekvering av kod och en rekommendation om att alla webbplatser som använder PHP ska uppdatera till den senaste PHP-versionen av ASAP ([fullständig varning finns här](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).

>[!WARNING]
>
>Observera att uppgraderingar av tjänster inte kan implementeras i produktionsmiljön utan att vårt infrastrukturteam får 48 arbetstimmar varsel om detta på Adobe Commerce molninfrastruktur. Detta är nödvändigt eftersom vi måste se till att det finns en infrastruktursupporttekniker tillgänglig som kan uppdatera din konfiguration inom en önskad tidsram med minimala driftavbrott i din produktionsmiljö. Så 48 timmar före när dina ändringar behöver vara i produktion [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) med information om den nödvändiga uppgraderingen och den tidpunkt då du vill att uppgraderingen ska starta.

Läs vidare om du vill veta mer om konsekvenser och steg för Adobe Commerce webbplatser:

**Adobe Commerce är värd för vår molnprodukt**

Om du använder Adobe Commerce i molninfrastruktur kan du samarbeta med teknikteamet för att omdistribuera Adobe Commerce med början när som helst\* för att dra nytta av uppdateringen. Vi rekommenderar att Merchants slutför omdistributionen senast den 30 september för att undvika problem med PCI-kompatibilitet som kan uppstå till följd av dessa sårbarheter i slutet av månaden.

Ytterligare information om omdistribution av din molnwebbplats för den här uppdateringen:

* Om din webbplats fortfarande använder PHP version 7.0 måste du först uppgradera till en PHP-version som stöds innan du kan omdistribuera den för att kunna utnyttja dessa säkerhetsuppdateringar.
* Mer information om uppgradering av PHP finns [här](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) för 2.1.x/2.2.x.

\* *I tidigare versioner av den här artikeln och i vårt meddelande angavs 19 september, men våra team har slutfört sitt arbete i förväg.*

**Adobe Commerce på alla andra värdlösningar**

Eftersom Adobe Commerce förlitar sig på PHP rekommenderar vi att alla som använder Adobe Commerce granskar nödvändiga uppdateringar för PHP med sin värdleverantör. Vi rekommenderar också att Merchants slutför denna granskning och eventuella uppdateringar senast den 30 september för att undvika problem med PCI-kompatibilitet som kan uppstå till följd av dessa sårbarheter i slutet av månaden.

Mer information om andra värdlösningar för Adobe Commerce:

* Adobe Commerce version 2.0 eller 1.x som använder PHP-versioner före 7.1 eller senare har ingen officiell PHP-patch tillgänglig. Rekommenderad sökväg är att uppgradera PHP till en PHP-version som stöds.

Rekommenderade patchar för denna sårbarhet är:

* PHP 7.1: [https://www.php.net/ChangeLog-7.php\#7.1.32](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2: [https://www.php.net/ChangeLog-7.php\#7.2.22](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3: [https://www.php.net/ChangeLog-7.php\#7.3.9](https://www.php.net/ChangeLog-7.php#7.3.9)

Om du vill ha mer information om PHP och de senaste versionerna kan du besöka [PHP:s webbplats](https://www.php.net/). Om du har frågor eller vill ha mer information om de effektivaste strategierna för säkerhet kan du läsa vår [Security Best Practices Guide](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf).
