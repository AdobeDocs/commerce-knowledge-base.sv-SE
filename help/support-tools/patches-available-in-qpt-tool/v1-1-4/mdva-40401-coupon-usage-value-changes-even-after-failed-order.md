---
title: 'MDVA-40401: Kuponganvändningsvärdet ändras efter felbeställning'
description: Korrigeringen MDVA-40401 åtgärdar ett problem där kuponganvändningsvärdet ändras även efter en misslyckad beställning. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 är installerat. Korrigerings-ID är MDVA-40401. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: c497ee84-9c20-4c75-ad3a-3b71f699acbf
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40401: Kuponanvändningsvärdet ändras efter felbeställning

Korrigeringen MDVA-40401 åtgärdar ett problem där kuponganvändningsvärdet ändras även efter en misslyckad beställning. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 har installerats. Korrigerings-ID är MDVA-40401. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användare kan inte återanvända kupongen när de har använt den i en misslyckad ordning.

<u>Steg som ska återskapas</u>:

1. Skapa en kundvagnsregel med automatiskt genererade kuponger.
1. Lägg en produkt i kundvagnen och använd kupongen.
1. Gå till **Utcheckning**.
1. Gör den tillagda produkten &quot;i lager&quot; innan du lägger ordern.
1. Du bör få ett *-fel ur lager*.
1. Spring cron.
1. Gå till kundvagnen och ta bort produkten.
1. Lägg till en annan produkt och tillämpa kupongen.

<u>Förväntade resultat</u>:

Kupongkoden ska gälla eftersom föregående order inte placerades.

<u>Faktiska resultat</u>:

Du får en *kupongkod*-fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
