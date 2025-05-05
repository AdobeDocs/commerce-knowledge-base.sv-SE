---
title: Leta efter Adobe Commerce-problem med verktyget för kvalitetskorrigeringar
description: I den här artikeln finns en översikt över QPT (Quality Patches Tool) och länkar till resurser som förklarar hur verktyget används.
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: ce9c69e12d64b4b4a8e6129783d9b15e95eff867
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Leta efter Adobe Commerce-problem med verktyget för kvalitetskorrigeringar

I den här artikeln finns en översikt över QPT (Quality Patches Tool) och länkar till resurser som förklarar hur verktyget används.

## Berörda produkter och versioner

* Adobe Commerce lokalt, alla [versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce i molninfrastrukturen, alla [versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Vad är verktyget för kvalitetspatchar?

[QPT-verktyget ](https://github.com/magento/quality-patches) (Quality Patches Tool) är enskilda korrigeringsfiler som utvecklats av Adobe och Magento Open Source-communityn.

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

Se [Verktyget för kvalitetskorrigeringar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i utvecklardokumentationen för en lista över tillgängliga korrigeringsfiler.

## Installera och använda verktyget för kvalitetspatchar

Installations- och användningskommandona skiljer sig åt för Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen, eftersom QPT-paketet ingår i paketet med komponentverktyg för molnet.

### Installera och använda QPT för Adobe Commerce lokalt

Mer information om hur du installerar och använder QPT för att tillämpa och återställa korrigeringsfiler finns i [Programuppdateringsguiden > Lappa](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i utvecklardokumentationen.

### Installera och använda QPT för Adobe Commerce i molninfrastrukturen

Mer information om hur du installerar och använder QPT för att tillämpa och återställa korrigeringsfiler på Adobe Commerce i molninfrastrukturen finns i [Cloud for Adobe Commerce > Tillämpa korrigeringsfiler](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i utvecklardokumentationen.

## Relaterad läsning

* [Versionsinformation för verktyget Kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/release-notes) i utvecklardokumentationen.
* [Använda Composer-korrigeringar från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

