---
title: '"MDVA-43718: Felet "konsument inte har behörighet att komma åt resurser" visas vid åtkomst till delad katalog"'
description: MDVA-43718-korrigeringen löser problemet där felet *konsumenten inte har behörighet att komma åt %resources.* visas vid åtkomst till en delad katalog från en anpassad integrering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Patch-ID:t är MDVA-43718. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: fa783ed4-906e-4ee6-b82a-cfe6db5ae89e
feature: Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43718: Felet &quot;konsumenten har inte behörighet att komma åt resurser&quot; visas vid åtkomst till delad katalog

MDVA-43718-korrigeringen löser problemet där felet *konsument har inte behörighet att komma åt %resources.* visas när du öppnar en delad katalog från en anpassad integrering. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Patch-ID:t är MDVA-43718. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Följande fel visas när du öppnar en delad katalog från en anpassad integrering: *Konsumenten har inte behörighet att komma åt %resources*.

<u>Steg som ska återskapas</u>:

1. Skapa en ny integrering från administratören > **System** > **Integrering** > **Lägg till integrering**.
1. Lägg till åtkomst för följande resurser och aktivera integreringen:

   * Magento_SharedCatalog::list
   * Magento_SharedCatalog::manage
   * Magento_Catalog::catalog

1. Med integreringsåtkomst: `rest/default/V1/sharedCatalog/1`

<u>Förväntade resultat</u>:

Information om den delade katalogen returneras.

<u>Faktiska resultat</u>:

Följande fel returneras:

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
