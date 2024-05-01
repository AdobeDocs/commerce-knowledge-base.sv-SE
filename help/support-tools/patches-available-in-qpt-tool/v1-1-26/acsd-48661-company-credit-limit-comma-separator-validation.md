---
title: 'ACSD-48661: Verifieringsfel för kommaavgränsare för företagskreditgräns'
description: Använd patchen ACSD-48661 för att åtgärda Adobe Commerce-problemet där företagets kreditgräns är större än 999, kommaavgränsaren förhindrar att företaget sparas på grund av ett valideringsfel.
exl-id: 85c5a93f-76c5-439b-adcc-511f8473f302
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-48661: Verifieringsfel för kommaavgränsare för företagskreditgräns

Korrigeringen ACSD-48661 åtgärdar ett problem där kommaavgränsaren förhindrar att företaget sparas när företagets kreditgräns är större än 999 på grund av ett valideringsfel. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 är installerat. Korrigerings-ID är ACSD-48661. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När företagets kreditgräns är större än 999 förhindrar kommaavgränsaren företaget från att spara på grund av ett valideringsfel.

<u>Steg som ska återskapas</u>:

1. Aktivera företagsfunktionen på **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Skapa ett företag och lägg till en kreditgräns som är större än 999 under **[!UICONTROL Company Credit]** -fliken.
1. Spara företaget.
1. Redigera företaget och försök spara det igen.

<u>Förväntade resultat</u>:

Du kan spara företaget utan att fastställa kreditgränsen. Komma stöds inte för indatafält för belopp och priser.

<u>Faktiska resultat</u>:

Du kan inte spara företaget på grund av ett valideringsfel i *[!UICONTROL Credit Limit]* fält. Adobe Commerce lägger automatiskt till kommaavgränsare för kreditgränser trots att [!UICONTROL Credit Limit] -fältet accepterar inte kommatecken.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
