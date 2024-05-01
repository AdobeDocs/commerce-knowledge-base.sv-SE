---
title: 'MDVA-32739-korrigering: gamla e-postmeddelanden skickas när asynkron sändning är aktiverad'
description: Korrigeringen MDVA-32739 åtgärdar ett problem där aktivering av [asynkrona e-postmeddelanden](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications) skickar gamla e-postmeddelanden. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.2.
exl-id: 8cf4ef8a-f2f2-47fb-9f69-0eedcc10ba8b
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-32739-korrigering: Gamla e-postmeddelanden skickas när asynkron sändning är aktiverad

MDVA-32739-korrigeringen åtgärdar ett problem där aktivering [asynkrona e-postmeddelanden](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications) skickar ut gamla e-postmeddelanden. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Inaktivera asynkron e-postsändning.
1. Skapa en beställning och kontrollera att e-postmeddelandet inte kan skickas.
1. Aktivera asynkron sändning.

<u>Förväntade resultat</u>:

E-postmeddelanden skickas endast för de order, leveranser, fakturor och kreditnotor som skapades efter den senaste asynkrona sändningsuppdateringen.

<u>Faktiska resultat</u>:

Det gamla e-postmeddelandet kommer att skickas ut via cronjob.

## Korrigera

När korrigeringen ingår i korrigeringen väljer Adobe Commerce order som skapas efter att den asynkrona sändningsmetoden senast har körts och skickar e-postmeddelandet för sådana order.

Som standard väljs den med en förskjutning på -1 dag.

Du kan ändra det här värdet (till exempel -2 dagar) genom att ändra `di.xml`.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
