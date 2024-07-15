---
title: 'ACSD-51892: Prestandaproblem där konfigurationsfiler läses in flera gånger'
description: Använd korrigeringsfilen ACSD-51892 för att åtgärda prestandaproblem i Adobe Commerce där konfigurationsfiler läses in flera gånger under distributionen.
feature: Observability
role: Admin
exl-id: 397343df-360f-43c4-bcef-be5f0da5aeef
source-git-commit: 97734799a39f41d0d6441379e21608fa5fcd1d4c
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-51892: Prestandaproblem där konfigurationsfiler läses in flera gånger

Korrigeringen ACSD-51892 åtgärdar det prestandaproblem som uppstår när `app/etc/env.php`- och `app/etc/config.php`-filer läses in varje gång konfigurationsvärden för distributionen nås inom en enda begäran. Den överdrivna filläsningen sätter press på systemet, vilket leder till försämrade prestanda. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 har installerats. Korrigerings-ID är ACSD-51892. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6-p2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det finns ett prestandaproblem där konfigurationsfilerna läses in flera gånger.

<u>Steg som ska återskapas</u>:

1. Installera eller uppgradera till Adobe Commerce 2.4.6 eller senare.
1. Kontrollera filsystemets loggar för åtkomst till `app/etc/env.php`- och `app/etc/config.php`-filer när distributionen körs.

<u>Förväntade resultat</u>:

Distributionen slutförs inom den vanliga tidsramen.

<u>Faktiska resultat</u>:

* Servrarna har problem med att svara på de kommandon du anger. Detta resulterar i *Error 503 first byte-timeout* vid åtkomst till webbplatsen.
* Det finns flera poster i loggfiler med åtkomst till `app/etc/env.php`- och `app/etc/config.php`-filer.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
