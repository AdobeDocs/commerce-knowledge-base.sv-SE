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

Korrigeringen ACSD-51892 åtgärdar det prestandaproblem som uppstår när programmet läses in `app/etc/env.php` och `app/etc/config.php` filer varje gång konfigurationsvärden för distribution används i en enda begäran. Den överdrivna filläsningen sätter press på systemet, vilket leder till försämrade prestanda. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 är installerat. Korrigerings-ID är ACSD-51892. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6-p2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det finns ett prestandaproblem där konfigurationsfilerna läses in flera gånger.

<u>Steg som ska återskapas</u>:

1. Installera eller uppgradera till Adobe Commerce 2.4.6 eller senare.
1. Kontrollera filsystemets loggar för åtkomst till `app/etc/env.php` och `app/etc/config.php` filer när distributionen körs.

<u>Förväntade resultat</u>:

Distributionen slutförs inom den vanliga tidsramen.

<u>Faktiska resultat</u>:

* Servrarna har problem med att svara på de kommandon du anger. Detta resulterar i *Fel 503, timeout för första byte* när du besöker webbplatsen.
* Det finns flera poster i loggfiler med åtkomst `app/etc/env.php` och `app/etc/config.php` filer.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
