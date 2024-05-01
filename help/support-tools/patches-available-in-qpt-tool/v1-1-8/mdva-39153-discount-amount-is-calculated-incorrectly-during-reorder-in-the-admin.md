---
title: 'MDVA-39153: Rabattbeloppet beräknas felaktigt vid omsortering i Admin'
description: Korrigeringen MDVA-39153 åtgärdar ett problem där rabattbeloppet beräknas felaktigt vid omsortering i Admin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 är installerat. Korrigerings-ID är MDVA-39153. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: d4d11bea-a528-4eb5-8a57-8a7330975e4a
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-39153: Rabattbeloppet beräknas felaktigt vid omsortering i administratören

Korrigeringen MDVA-39153 åtgärdar ett problem där rabattbeloppet beräknas felaktigt vid omsortering i Admin. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 är installerat. Korrigerings-ID är MDVA-39153. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Rabattbeloppet beräknas felaktigt under omsorteringen i administratören.

<u>Steg som ska återskapas</u>:

1. Gå till **Administratör** > **Lager** > **Konfiguration** > **Försäljning** > **Skatter**.
1. Aktivera moms för frakt och visa momsen i kundvagnen.
1. Aktivera och konfigurera metoden för tabellradsleverans ($15).
1. Skapa en momsregel för inbyggd momssats (för CA).
1. Skapa en kundvagnsprisregel med en fast rabatt på 5 USD som tillämpas på hela vagnen och fraktbeloppet.
1. Lägg en produkt till priset 12 USD i kundvagnen och gå till sidan Kundvagn.
1. Använd rabatten på kundvagnen.
1. Ställ in leveransmetoden i avsnittet &quot;Beräkningar&quot; till &quot;Schablonbelopp&quot;.
1. Gå igenom kassan till granskningsstegen (placera inte ordern).
1. Gå till hemsidan och sedan tillbaka till kundvagnen.
1. Ändra leveranssätt i avsnittet &quot;Beräkningar&quot; till &quot;Tabellhastighet&quot;.

<u>Förväntade resultat</u>:

Rabatten är densamma - 5 USD.

<u>Faktiska resultat</u>:

Rabatten är 6,31 USD.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
