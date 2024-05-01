---
title: 'MDVA-30265: tracking link in email returns 404 Page not found'
description: MDVA-30265-korrigeringen löser problemet med felet"404 Page not found" när kunden klickar på länken för leveransspårning i orderbekräftelsemeddelandet. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 53e1ca98-dfa0-445b-a71a-56fd01b630ec
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# MDVA-30265: spårningslänk i e-postreturer returnerar 404 Sidan hittades inte

MDVA-30265-korrigeringen löser problemet med felet&quot;404 Page not found&quot; när kunden klickar på länken för leveransspårning i orderbekräftelsemeddelandet. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3 till 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När leveransen har skapats för en beställning skickas ett e-postmeddelande med spårningsinformation och en länk för att spåra beställningen till kunden. När kunden klickar på länken för leveransspårning i e-postmeddelandet returneras felet&quot;404 Sidan hittades inte&quot;.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce 2.4. Om du vill se steg går du till [Installera Adobe Commerce med Composer](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) i vår dokumentation för utvecklare.
1. Beställ.
1. Gå till administrationspanelen > **Försäljning** > **Beställningar**. Leta efter den order du just skapade och öppna den.
1. Skapa en leverans och lägg till ett spårningsnummer (transportör = anpassat värde). Om du vill se steg går du till [Orderhantering > Skapa en leverans](https://docs.magento.com/user-guide/sales/shipments-create.html) i vår användarhandbok.
1. Du får ett e-postmeddelande. Klicka på spårningslänken för att kontrollera om den fungerar.
1. Skapa en faktura. Om du vill se steg går du till [Orderhantering > Skapa en faktura](https://docs.magento.com/user-guide/sales/invoice-create.html) i vår användarhandbok. Klicka sedan igen på spårningslänken ovan.

<u>Förväntade resultat</u>:

Spårningslänken ska fungera även efter att fakturan har skapats.

<u>Faktiska resultat</u>:

När du har skapat fakturan fungerar inte spårningslänken och returnerar felsidan&quot;404 Sidan hittades inte&quot;.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
