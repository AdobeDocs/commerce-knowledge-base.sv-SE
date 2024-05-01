---
title: '''ACSD-53583: Förbättra prestanda för partiell omindexering för [!UICONTROL Category Products] och [!UICONTROL Product Categories] indexerare'
description: Använd patchen ACSD-53585 för att förbättra prestandan för partiell omindexering för kategoriprodukter och produktkategoriindexerare.
feature: Products, Categories
role: Admin, Developer
exl-id: 1c8f7df3-379f-42d6-8b41-286d34f725d2
source-git-commit: 29c2918ccae6404f6ae87d360ac16b149de5dd0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53583: Förbättra partiell indexering för indexerare för kategoriprodukter och produktkategorier

ACSD-53583-korrigeringen förbättrar den partiella omindexeringsprestandan för *Kategoriprodukter* och *Produktkategorier* indexerare. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.39 är installerat. Korrigerings-ID är ACSD-53583. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3
* Inte kompatibelt med [!DNL Live Search] -modul. Om du vill använda den här korrigeringen på [!DNL Live Search] begär ytterligare en ACSD-55719-patch för installationen.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ofullständig indexering tar längre tid än fullständig indexering.

<u>Steg som ska återskapas</u>:

1. Omvandla alla index till *Uppdatera efter schema*.
1. Generera data med [!DNL Performance Toolkit] (medelprofil).
1. Gör ändringar i alla produkter och kategorier så att de ligger i indexeftersläpningen och alla index är inaktiva.
1. Utför partiell omindexering för *Kategoriprodukter* och *Produktkategorier* indexerare.

<u>Förväntade resultat</u>:

Ofullständig indexering anropas en gång per produkt och tar nästan samma tid som en fullständig indexering eftersom alla produkter och kategorier har ändrats.

<u>Faktiska resultat</u>:

Partiell omindexering anropas många gånger per produkt och tar längre tid än fullständig omindexering.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
