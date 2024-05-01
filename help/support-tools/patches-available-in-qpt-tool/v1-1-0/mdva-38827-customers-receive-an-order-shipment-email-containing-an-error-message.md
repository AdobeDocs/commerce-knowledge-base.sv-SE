---
title: 'MDVA-38827: Kunderna får orderleveransfel via e-post'
description: "MDVA-38827-korrigeringen åtgärdar ett problem där kunderna får ett e-postmeddelande om orderleverans med följande felmeddelande: *Ett fel uppstod när innehållet genererades*. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0 är installerat. Patch-ID:t är MDVA-38827. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4."
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827: Kunderna får orderleveransfel via e-post

MDVA-38827-korrigeringen åtgärdar ett problem där kunderna får ett e-postmeddelande med följande felmeddelande: *Ett fel uppstod när innehållet genererades*. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0 är installerat. Patch-ID:t är MDVA-38827. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.4.2-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När alternativet Meddela kunder via e-post för leverans har valts får kunderna ett e-postmeddelande med följande felmeddelande: *Ett fel uppstod när innehållet genererades*.

<u>Steg som ska återskapas</u>:

1. Gå till **Marknadsföring** > **Kommunikation** > **E-postmallar** och markera **Lägg till ny mall**.
   * Välj **Magento Sales** > **Ny utleverans**.
   * Klicka på **Läs in mall**.
   * Lägg till ett mallnamn (till exempel Core Shipping Template) och klicka på **Spara**.
1. Gå till **Butik** > Inställningar > **Konfiguration** > **Försäljning** > **E-postadress**:
   * Aktivera **Leveranskommentarer**.
   * Välj **Core Shipping Template** (se avsnittet&quot;Lägg till ett mallnamn&quot; i steg 1) under E-postmall för försändelsekommentar och E-postmall för försändelsekommentar för gäst.
1. Beställ. Gå till administrationspanelen > **Försäljning** > **Beställning**, klicka **Visa** och skicka sedan ordern.
1. Orderstatusen ändras från Väntande till Bearbetning.
1. Klicka **Leveranser** på vänster sidofältsmeny och sedan klicka **Visa** för att se ordningen.
1. Lägg till en kommentar i **Kommentar** nedan **Leveranshistorik** och markera kryssrutan **Meddela kunden via e-post**.
1. Klicka **Skicka kommentar**.

<u>Förväntade resultat</u>:

E-postförsäljning med försändelsekommentarer genereras.

<u>Faktiska resultat</u>:

Följande felmeddelande tas emot i e-postmeddelandet: *Ett fel uppstod när det här innehållet genererades.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
