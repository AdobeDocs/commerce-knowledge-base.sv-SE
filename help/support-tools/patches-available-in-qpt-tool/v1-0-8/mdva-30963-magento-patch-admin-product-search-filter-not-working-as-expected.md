---
title: 'MDVA-30963: Sökfiltret för admin-produkten fungerar inte som förväntat'
description: Korrigeringen MDVA-30963 löser problemet där Commerce Admin och produktsökfiltret inte fungerar som förväntat. Värden som åsidosätts i en butiksvy beaktas också vid filtrering på **All butiksvy**. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: bde2836e-8954-48e5-b411-08c951ec8620
feature: Admin Workspace, Products, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# MDVA-30963: Sökfiltret för admin-produkten fungerar inte som förväntat

Korrigeringen MDVA-30963 löser problemet där Commerce Admin och produktsökfiltret inte fungerar som förväntat. Värden som åsidosätts i en butiksvy beaktas också vid filtrering i lagringsvyns omfång **Alla butiksvyer** . Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce om molninfrastruktur 2.4.0

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.2 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Ange **Lagrar** > **Konfiguration** > **Katalog** > **Katalog** > **Pris** > **Katalogens prisomfång** = *Webbplats*.
1. Skapa två webbplatser med två olika valutor (standardwebbplatsen är till exempel en Indienbutik \[rupee ₹\] och den andra är en USA-butik \[dollar $\]).
1. Ange följande **basvaluta**, **standardvisningsvaluta** och **tillåtna valutor**:
   * **Standardkonfiguration** = *USD (standard)*
   * **Huvudwebbplats** = *Indiska rupee*
   * **WebsiteUS** = **Använd standard** = *USD*
1. Ange **Lagrar** > **Valutakurser** = *1:1*.
1. Skapa en enkel testprodukt som tilldelats båda webbplatserna till följande priser:
   * **Standardpris** = **US Website price** = *123 USD*
   * **Pris på webbplatsen** = *321 rupee*
1. Skapa en subAdmin-användare som bara har åtkomst till USA Store.
1. Gå till den amerikanska butiken och placera en produkt i kundvagnen (Exempel: *123 USD-pris*).
1. Logga in på Admin med subAdmin som just skapats (Exempel: *Endast USA-administratör*).
1. Gå till **Rapporter** > **Produkter i kundvagn**.

<u>Förväntade resultat</u>:

När du filtrerar i butiksvyns **alla butiksvy** bör produktfiltrering hämta det angivna värdet i det aktuella omfånget.

<u>Faktiska resultat</u>:

Värden som åsidosätts i en butiksvy beaktas också vid filtrering i butiksvyns visningsomfång &quot;All store view&quot;.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
