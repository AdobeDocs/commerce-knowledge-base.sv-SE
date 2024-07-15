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

Korrigeringen ACSD-48661 åtgärdar ett problem där kommaavgränsaren förhindrar att företaget sparas när företagets kreditgräns är större än 999 på grund av ett valideringsfel. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 har installerats. Korrigerings-ID är ACSD-48661. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När företagets kreditgräns är större än 999 förhindrar kommaavgränsaren företaget från att spara på grund av ett valideringsfel.

<u>Steg som ska återskapas</u>:

1. Aktivera företagsfunktionen på **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Skapa ett företag och lägg till en kreditgräns som är större än 999 på fliken **[!UICONTROL Company Credit]**.
1. Spara företaget.
1. Redigera företaget och försök spara det igen.

<u>Förväntade resultat</u>:

Du kan spara företaget utan att fastställa kreditgränsen. Komma stöds inte för indatafält för belopp och priser.

<u>Faktiska resultat</u>:

Du kan inte spara företaget på grund av ett valideringsfel i fältet *[!UICONTROL Credit Limit]*. Adobe Commerce lägger automatiskt till kommaavgränsare för kreditgränser även om fältet [!UICONTROL Credit Limit] inte accepterar kommatecken.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
