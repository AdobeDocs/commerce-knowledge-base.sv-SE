---
title: 'MC-41359 commerce patch: missing settings SameSite cookie param'
description: Handelskorrigeringen för MC-41359 åtgärdar ett problem med att inställningarna för SammaSite-cookie-parametrar saknas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Korrigerings-ID är MC-41359. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: b48faa3f-0d9a-4d65-9abb-1573c6240635
feature: Observability
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# MC-41359 Commerce patch: Inställningar som saknas för SameSite cookie param

Handelskorrigeringen för MC-41359 åtgärdar ett problem med att inställningarna för SammaSite-cookie-parametrar saknas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Korrigerings-ID är MC-41359. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.4.2

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce lokalt och Adobe Commerce i molninfrastruktur 2.3.6-p1, 2.4.2, 2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Inställningar för parametern SameSite cookie saknas.

<u>Steg att återskapa:</u>

Förutsättningar:

* Öppna Chrome och gå till chrome://flags/
* Aktivera **SameSite som standard måste cookies** och **Cookies utan SameSite vara säkra**.
* Öppna Chrome-kontrollen.

<u>Scenario 1:</u>

1. Aktivera PayPal.
1. Gå till butiken.
1. Lägg en produkt i kundvagnen.
1. Gå till kassan.

<u>Scenario 2:</u>

Om du har New Relic [aktiverat](https://docs.magento.com/user-guide/reports/new-relic-reporting.html) visas en varning på alla sidor på en frontend.

<u>Faktiskt resultat:</u>

Varningsmeddelande i webbläsarkonsolen: *En cookie som är associerad med en korsresurs har angetts utan ett SameSite-attribut.*

<u>Förväntat resultat:</u>

&quot;lax&quot; ska inte läggas till i cookie-domänen. Samma platsattribut ska finnas med standardvärdet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar som finns i QPT-verktyget](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i utvecklardokumentationen.
