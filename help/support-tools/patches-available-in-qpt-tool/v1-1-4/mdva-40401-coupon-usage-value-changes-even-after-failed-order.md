---
title: 'MDVA-40401: Kuponganvändningsvärdet ändras efter felbeställning'
description: Korrigeringen MDVA-40401 åtgärdar ett problem där kuponganvändningsvärdet ändras även efter en misslyckad beställning. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 är installerat. Korrigerings-ID är MDVA-40401. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: c497ee84-9c20-4c75-ad3a-3b71f699acbf
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40401: Kuponanvändningsvärdet ändras efter felbeställning

Korrigeringen MDVA-40401 åtgärdar ett problem där kuponganvändningsvärdet ändras även efter en misslyckad beställning. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 är installerat. Korrigerings-ID är MDVA-40401. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användare kan inte återanvända kupongen när de har använt den i en misslyckad ordning.

<u>Steg som ska återskapas</u>:

1. Skapa en kundvagnsregel med automatiskt genererade kuponger.
1. Lägg en produkt i kundvagnen och använd kupongen.
1. Gå till **Utcheckning**.
1. Gör den tillagda produkten &quot;i lager&quot; innan du lägger ordern.
1. Du borde skaffa en *slut på lager* fel.
1. Spring cron.
1. Gå till kundvagnen och ta bort produkten.
1. Lägg till en annan produkt och tillämpa kupongen.

<u>Förväntade resultat</u>:

Kupongkoden ska gälla eftersom föregående order inte placerades.

<u>Faktiska resultat</u>:

Du får en *kupongkoden är ogiltig* fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
