---
title: Problem med beredskapskontroll av PHP-version
description: I den här artikeln beskrivs lösningar på problem med PHP-versionen som du kan stöta på när du installerar/uppgraderar Adobe Commerce lokalt med hjälp av webbinstallationsguiden.
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Problem med beredskapskontroll av PHP-version

I den här artikeln beskrivs lösningar på problem med PHP-versionen som du kan stöta på när du installerar/uppgraderar Adobe Commerce lokalt med hjälp av webbinstallationsguiden.

>[!WARNING]
>
>Observera att uppgraderingar av tjänster inte kan implementeras i produktionsmiljön utan att vårt infrastrukturteam får 48 arbetstimmar varsel om detta på Adobe Commerce molninfrastruktur. Detta är nödvändigt eftersom vi måste se till att det finns en infrastruktursupporttekniker tillgänglig som kan uppdatera din konfiguration inom en önskad tidsram med minimala driftavbrott i din produktionsmiljö. Så 48 timmar före när ändringarna måste vara i produktion [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) ange vilken serviceuppgradering du behöver och ange när du vill att uppgraderingen ska starta.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## PHP-versionen stöds inte

### Problem

Kontrollen misslyckas eftersom du använder en PHP-version som inte stöds.

### Lösning

Du löser det här problemet genom att använda en av de versioner som stöds i utvecklardokumentationen [2.3.x Systemkrav](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html) och [2.2.x Systemkrav](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html).

## PHP-beredskapskontrollen visas inte

### Problem

PHP-beredskapskontrollen visar inte PHP-versionen som på bilden nedan.
![upgr-tshot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### Lösning

Det här är ett symtom på en felaktig inställning av kronjobb. Mer information finns i [Ställ in cron-jobb](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) i vår dokumentation för utvecklare.

## Felaktig PHP-version

### Problem

Kontrollen rapporterar fel PHP-version. Vanligtvis händer detta bara för avancerade användare som har flera PHP-versioner installerade. I vissa fall misslyckas beredskapskontrollen, i andra fall kan den misslyckas.

Om PHP-versionen som rapporterats av beredskapskontrollen är felaktig beror det på att PHP-versionerna inte matchar PHP-pluginmodulen för PHP och webbservern. Adobe Commerce kräver att du använder *en version* PHP för både CLI (som kör cron) och webbservern (som kör Commerce Admin, Component Manager och System Upgrade).

### Lösning

Vi antar att om du har det här problemet är du en avancerad användare som troligen har installerat flera versioner av PHP på datorn.

Försök med följande för att lösa problemet:

* Starta om webbservern eller php-fm.
* Kontrollera `$PATH` miljövariabel för flera sökvägar till PHP.
* Använd `which php` för att hitta den första körbara PHP-filen i sökvägen. Om den inte är korrekt tar du bort den eller skapar en länk till rätt PHP-version.
* Använd en [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) sida för att samla in mer information.
* Se till att du kör en PHP-version som stöds enligt våra systemkrav i vår utvecklardokumentation:
   * [Adobe Commerce 2.3.x - systemkrav](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html)
   * [Adobe Commerce 2.2.x - systemkrav](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html)
* Ange samma PHP-inställningar för både PHP-kommandoraden och PHP-webbserverns plugin-program enligt beskrivningen i [Konfigurationsalternativ för PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-centos-ubuntu.html) i vår dokumentation för utvecklare.
