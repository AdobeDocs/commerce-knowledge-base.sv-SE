---
title: 'MDVA-40311: Felet "Ogiltig säkerhet eller formulärnyckel" efter inloggning i Admin om anpassad administratörssökväg har konfigurerats'
description: 'Korrigeringen MDVA-40311 åtgärdar ett fel där administratörsanvändaren får ett felmeddelande: *Ogiltig säkerhet eller formulärnyckel. Uppdatera sidan* efter inloggning i administratören om den anpassade administratörssökvägen är konfigurerad och den hemliga nyckeln är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 är installerat. Korrigerings-ID är MDVA-40311. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4."'
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311: Felet &quot;Ogiltig säkerhet eller formulärnyckel&quot; efter inloggning i Admin om anpassad administratörssökväg har konfigurerats

Korrigeringen MDVA-40311 åtgärdar ett problem där administratörsanvändaren får ett felmeddelande: *Ogiltig säkerhets- eller formulärnyckel. Uppdatera sidan* efter inloggning i Admin om den anpassade administratörssökvägen har konfigurerats och den hemliga nyckeln har aktiverats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 har installerats. Korrigerings-ID är MDVA-40311. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren får ett felmeddelande: *Ogiltig säkerhets- eller formulärnyckel. Uppdatera sidan* efter inloggning i Admin om den anpassade administratörssökvägen har konfigurerats och den hemliga nyckeln har aktiverats.

<u>Steg som ska återskapas</u>:

* Logga in som Admin-användare med ett giltigt användarnamn och lösenord.

<u>Förväntade resultat</u>:

Användaren kan logga in utan något felmeddelande.

<u>Faktiska resultat</u>:

*Ogiltig säkerhets- eller formulärnyckel. Uppdatera felmeddelandet på sidan* visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
