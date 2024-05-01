---
title: 'MDVA-36464: Skicka e-postinställningar som inte fungerar på butiksvisningsnivå'
description: Korrigeringen MDVA-36464 åtgärdar ett problem där inställningarna för att skicka e-post inte fungerar på butiksvisningsnivå. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Korrigerings-ID är MDVA-36464. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: cdf7e208-90ee-4711-8407-026da42fe3c8
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-36464: Skicka e-postinställningar som inte fungerar på butiksvisningsnivå

Korrigeringen MDVA-36464 åtgärdar ett problem där inställningarna för att skicka e-post inte fungerar på butiksvisningsnivå. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Korrigerings-ID är MDVA-36464. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.4.0-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Krav:</u>

Installera rena Adobe Commerce.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en webbplats-, butik- och butiksvy (i det här exemplet är den andra webbplatsen *webbplats2*).
1. Inaktivera **E-postmeddelande** på global nivå i **Butik** > **Konfig** > **Avancerat** > **System** > **Inställningar för att skicka e-post**.
1. Aktivera **E-postmeddelande** på *webbplats2* level (**Inaktivera e-postkommunikation** = *Nej*).
1. Skapa en ny användare i Admin och tilldela den till *webbplats2*.
1. Gå till Admin och klicka på **Återställ lösenord** för kunden som skapas ovan i steg 4.

<u>Förväntade resultat</u>:

Båda **välkomstmeddelande** och **återställ e-postadress för lösenord** skickas som förväntat eftersom **Inaktivera e-postkommunikation** = *Nej* för den andra webbplatsen (Exempel: *webbplats2*).

<u>Faktiska resultat</u>:

* The **välkomstmeddelande** efter det att den nya kunden har skapats inte aktiveras.
* The **återställ e-postadress för lösenord** aktiveras inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
