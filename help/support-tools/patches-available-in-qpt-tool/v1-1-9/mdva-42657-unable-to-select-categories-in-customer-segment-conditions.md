---
title: 'MDVA-42657: Det går inte att välja kategorier i villkoren för kundsegmentet'
description: MDVA-42657-korrigeringen löser problemet där administratörsanvändaren inte kan välja kategorier under kundsegmentsvillkoren. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 är installerat. Korrigerings-ID är MDVA-42657. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 9c810dcd-b39b-4456-a362-5452ada4dc53
feature: Categories, Console, Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-42657: Det går inte att välja kategorier i villkoren för kundsegmentet

MDVA-42657-korrigeringen löser problemet där administratörsanvändaren inte kan välja kategorier under kundsegmentsvillkoren. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 är installerat. Korrigerings-ID är MDVA-42657. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren kan inte välja kategorier i kundsegmentsvillkoren.

<u>Steg som ska återskapas</u>:

1. Gå till **Kunder** > **Segment**.
1. Skapa ett nytt segment.
1. Gå till det nya segmentet och klicka på **Villkor** till vänster i navigeringen.
1. Klicka på det gröna plustecknet.
1. Välj Produkthistorik under Produkter.
1. Ändra&quot;visade&quot; till&quot;ordnade&quot;.
1. Ändra&quot;ALL&quot; till&quot;ANY&quot;.
1. Klicka på det kapslade gröna plustecknet och välj Kategori.
1. Klicka på **...** och klicka sedan på väljarikonen (till vänster om bockmarkeringen).
1. Öppna webbläsarens dev-konsol.
1. Markera kryssrutorna för någon/flera kategorier och notera javascript-felet som genereras i konsolen.
1. Klicka på **Spara** -knappen.
1. Navigera tillbaka till villkoret och kontrollera om de valda kategorierna har sparats.

<u>Förväntade resultat</u>:

De valda kategorierna sparas och markeras när segmentvillkoren visas/redigeras.

<u>Faktiska resultat</u>:

De valda kategorierna saknas och sparades inte korrekt. Följande fel visas i konsolen:

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
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
