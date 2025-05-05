---
title: 'MDVA-42520: Skattesats som tillämpas två gånger när "Aktivera gränsöverskridande handel" används'
description: MDVA-42520-korrigeringen åtgärdar ett problem där skattesatsen tillämpas två gånger när **Enable Cross Border Trade** används. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 är installerat. Korrigerings-ID är MDVA-42520. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: c1ca44eb-fe92-4f28-807a-3a4563433386
feature: Catalog Management, Orders, Taxes
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-42520: Skattesats som tillämpas två gånger när&quot;Aktivera gränsöverskridande handel&quot; används

Korrigeringen MDVA-42520 åtgärdar ett problem där momssatsen tillämpas två gånger när **Aktivera gränsöverskridande handel** används. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 är installerat. Korrigerings-ID är MDVA-42520. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Skattesatsen tillämpas två gånger när **Aktivera gränsöverskridande handel** används.

<u>Steg som ska återskapas</u>:

1. Aktivera **Företag**, **Delad katalog** och **Citat**
1. Konfigurera moms enligt skärmbilden. Se till att du aktiverar **Gränsöverskridande handel**.

   ![skatteinställningar](/help/support-tools/patches-available-in-qpt-tool/assets/tax_settings_1.png){width="700"}

1. Skapa en skattesats för Tyskland (10 %).
1. Skapa en momsregel för att tillämpa momssatsen.
1. Skapa ett företag och en anpassad delad katalog.
1. Skapa en produkt med priset 100 och inkludera den i den anpassade delade katalogen med en prisrabatt på 20 %.
1. Skapa en kund med en tysk adress och tilldela den till företaget
1. Lägg till tio produkter på kortet som kund.
1. Gå till kundvagnen och begär en offert.
1. Öppna offerten på baksidan och försök lägga till ytterligare 10 % rabatt.

<u>Förväntade resultat</u>:

Offertdelsumma (inklusive skatt) och totalsumma för offert (inklusive skatt) = $720

<u>Faktiska resultat</u>:

Offertdelsumma (inklusive skatt) och totalsumma för offert (inklusive skatt) = 649,50 USD.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
