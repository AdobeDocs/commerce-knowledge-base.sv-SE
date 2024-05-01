---
title: "MDVA-44887: 'SyntaxError uncaught: Unexpected token const' error in Admin panel"
description: "MDVA-44887-korrigeringen åtgärdar ett problem där administratörsanvändaren inte kan klicka på något menyalternativ. *Ohanterat SyntaxError: Oväntat token const*-fel visas på Admin-panelen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Patch-ID:t är MDVA-44887. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5."
exl-id: 66555e66-49d0-4f80-8f77-84ee107ab12e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44887: Felet &#39;SyntaxError uncaught: Unexpected token const&#39; i Admin panel

MDVA-44887-korrigeringen åtgärdar ett problem där administratörsanvändaren inte kan klicka på något menyalternativ. The *Ohanterad SyntaxError: Oväntad tokenkonst* -fel visas på panelen Admin. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Patch-ID:t är MDVA-44887. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren kan inte klicka på något menyalternativ. The *Ohanterad SyntaxError: Oväntad tokenkonst* -fel visas på panelen Admin.

<u>Steg som ska återskapas</u>:

1. Aktivera JS-paketering.
1. Minimera JS-filerna.
1. Logga in på Commerce Admin-panelen.

<u>Förväntade resultat</u>:

Administratörsanvändaren kan inte klicka på något menyalternativ. Det finns ett fel i webbläsarkonsolen: *Ohanterad SyntaxError: Oväntad tokenkonst*.

<u>Faktiska resultat</u>:

Administratörspanelen är tillgänglig för en administratörsanvändare.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
