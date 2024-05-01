---
title: '"ACSD-47336: [!UICONTROL Something went wrong] fel vid stängning av meddelanden i Adobe Commerce Admin'
description: Använd korrigeringsfilen ACSD-47336 för att åtgärda Adobe Commerce-problemet där användaren ser [!UICONTROL Something went wrong] fel när meddelanden i [!DNL Commerce] Admin.
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336 _[!UICONTROL Something went wrong]_fel vid stängning av meddelanden i Adobe Commerce Admin

Korrigeringen ACSD-47336 åtgärdar ett problem där användaren ser _[!UICONTROL Something went wrong]_fel när meddelanden i [!DNL Commerce] Admin. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 är installerat. Korrigerings-ID är ACSD-47336. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder): 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren ser _[!UICONTROL Something went wrong]_fel när meddelanden i [!DNL Commerce] Admin.

<u>Steg som ska återskapas</u>:

1. Utför en gruppåtgärd (t.ex. satsvis uppdatering av produktattribut från produktrutnätet).
1. Slutför åtgärden (t.ex. kör `bin/magento queue:consumer:start product_action_attribute.update`).
1. Uppdatera [!DNL Commerce] Administratörssidan, expandera avsnittet med administratörsmeddelanden och klicka på **[!UICONTROL Dismiss All Completed Tasks]** länk.

<u>Förväntade resultat</u>:

The _[!UICONTROL Something went wrong]_fel ska inte visas när de slutförda uppgifterna rensas.

<u>Faktiska resultat</u>:

The _[!UICONTROL Something went wrong]_fel visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
