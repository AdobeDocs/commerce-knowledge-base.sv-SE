---
title: Leta efter Adobe Commerce-problem med verktyget för kvalitetskorrigeringar
description: I den här artikeln finns en översikt över QPT (Quality Patches Tool) och länkar till resurser som förklarar hur verktyget används.
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Leta efter Adobe Commerce-problem med verktyget för kvalitetskorrigeringar

I den här artikeln finns en översikt över QPT (Quality Patches Tool) och länkar till resurser som förklarar hur verktyget används.

## Berörda produkter och versioner

* Adobe Commerce lokalt, alla [versionerna](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce i molninfrastrukturen, alla [versionerna](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Vad är verktyget för kvalitetspatchar?

The [Verktyget Kvalitetspatchar](https://github.com/magento/quality-patches) (QPT) är individuella plåster som utvecklats av Adobe och Magento Open Source.

Du kan:

* lägg in kvalitetspatchar i paketet
* återställa tidigare använda patchar
* visa allmän information om kvalitetsuppdateringar för den installerade versionen av Adobe Commerce.

Här är ett exempel på statustabellen som du kan hämta för att visa tillgängliga korrigeringar:

![Magento_patches_list](assets/status_table.png)

Verktyget är avsett att göra det möjligt för dig att använda korrigeringsfiler för problem som du kan uppleva hos Adobe Commerce, eller att enkelt tillämpa korrigeringsfiler som Adobe Commerce support föreslår.

>[!NOTE]
>
>QPT är endast till för kvalitetspatchar. Säkerhetsuppdateringar finns i [Magento Security Center](https://magento.com/security/patches).

## Patchar tillgängliga i verktyget för kvalitetspatchar

Se [Verktyget Kvalitetspatchar](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation för att se en lista över tillgängliga korrigeringsfiler.

## Installera och använda verktyget för kvalitetspatchar

Installations- och användningskommandona skiljer sig åt för Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen, eftersom QPT-paketet ingår i paketet med komponentverktyg för molnet.

### Installera och använda QPT för Adobe Commerce lokalt

Se [Programuppdateringshandbok > Lappa](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation för mer information om hur du installerar och använder QPT för att tillämpa och återställa korrigeringsfiler.

### Installera och använda QPT för Adobe Commerce i molninfrastrukturen

Se [Cloud för Adobe Commerce > Använd korrigeringsfiler](https://devdocs.magento.com/cloud/project/project-patch.html) i utvecklardokumentationen om du vill ha mer information om hur du installerar och använder QPT för att tillämpa och återställa korrigeringsfiler på Adobe Commerce i molninfrastrukturen.

## Relaterad läsning

* [Versionsinformation om verktyget Kvalitetspatchar](https://devdocs.magento.com/quality-patches/release-notes.html) i vår dokumentation för utvecklare.
* [Använda Composer-korrigeringar från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.
