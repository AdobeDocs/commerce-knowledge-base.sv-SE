---
title: 'ACSD-49480: Ignorera efterföljande regler som inte fungerar'
description: Använd korrigeringsfilen ACSD-49480 för att åtgärda Adobe Commerce-problemet där [!UICONTROL Cart Price Rule - Discard Subsequent Rules] inte fungerar som det ska.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] fungerar inte som det ska

Korrigeringen ACSD-49480 åtgärdar ett fel där [!UICONTROL Cart Price Rule - Discard Subsequent Rules] inte fungerar som det ska. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.32 har installerats. Korrigerings-ID är ACSD-49480. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] fungerar inte som det ska.

<u>Steg som ska återskapas</u>:

1. Skapa en **[!UICONTROL Cart Price Rule]** med en kupongkod (kalla den för *TEST*) som ger en rabatt på $10 på *Product ID 1* på fliken **[!UICONTROL Actions]** med [!UICONTROL Discard Subsequent Rules] inställd på *[!UICONTROL Yes]* och [!UICONTROL Priority] inställd på *1*.
1. Skapa ytterligare **[!UICONTROL Cart Price Rule]** utan en kupongkod som ger *produkt-ID* $5 rabatt på fliken **[!UICONTROL Actions]** med [!UICONTROL Priority] inställd på *2*. Här antar vi att detta är en global försäljning av *produkt-ID 2*.
1. Gå till klientsidan och lägg till *produkt-ID* och *produkt-ID* i kundvagnen.
1. Använd kupongkoden *TEST*.

<u>Förväntade resultat</u>

* *Rabatt 1* tillämpas på *produkt-ID 1*.
* *Rabatt 2* tillämpas på *produkt-ID 2*.

<u>Faktiska resultat</u>

* Endast *Rabatt 1* tillämpas på *produkt-ID 1*.
* *Rabatt 2* används inte för *produkt-ID 2*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
