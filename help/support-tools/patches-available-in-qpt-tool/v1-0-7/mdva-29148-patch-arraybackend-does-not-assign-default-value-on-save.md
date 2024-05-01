---
title: 'MDVA-29148: ArrayBackend tilldelar inte standardvärde vid sparning'
description: MDVA-29148-korrigeringen löser problemet där "\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend" inte tilldelar standardvärdet när filen sparas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 7b2f5c18-0e7a-485b-a07e-700e435697fd
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-29148: ArrayBackend tilldelar inte standardvärde när det sparas

MDVA-29148-korrigeringen löser problemet där `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` tilldelar inte standardvärdet när filen sparas. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.3-p1.

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) >=2.3.0 &lt;2.4.2.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När en produkt skapas via ett importskript eller REST API, attribut som använder `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` serverdelsmodell med ett standardvärde tilldelas inte standardvärdet.

<u>Steg som ska återskapas</u>:

1. Skapa ett nytt globalt attribut som använder `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` serverdelsmodell och ett icke-tomt standardvärde.
1. Använd REST API för att skapa en ny produkt.
1. Hämta den nya produkten från REST API och bekräfta att attributet inte finns i produktens anpassade attribut.

<u>Förväntade resultat</u>:

Standardvärdet för det anpassade attributet sparades i produktattributet.

<u>Faktiska resultat</u>:

Standardvärdet för det anpassade attributet sparades inte i produktattributet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
