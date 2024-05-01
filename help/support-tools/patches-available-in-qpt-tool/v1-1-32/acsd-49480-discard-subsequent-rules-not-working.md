---
title: 'ACSD-49480: Ignorera efterföljande regler fungerar inte'
description: Använd programfixen ACSD-49480 för att åtgärda Adobe Commerce-problemet där [!UICONTROL Cart Price Rule - Discard Subsequent Rules] fungerar inte som det ska.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] fungerar inte som avsett

Korrigeringen ACSD-49480 åtgärdar ett problem där [!UICONTROL Cart Price Rule - Discard Subsequent Rules] fungerar inte som det ska. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.32 är installerat. Korrigerings-ID är ACSD-49480. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] fungerar inte som det ska.

<u>Steg som ska återskapas</u>:

1. Skapa en **[!UICONTROL Cart Price Rule]** med en kupongkod (namnge den som *TEST*) som ger rabatt på 10 dollar till *Produkt-ID 1* i **[!UICONTROL Actions]** tabba med [!UICONTROL Discard Subsequent Rules] ange till *[!UICONTROL Yes]* och [!UICONTROL Priority] ange till *1*.
1. Skapa en till **[!UICONTROL Cart Price Rule]** utan kupongkod som ger 5 USD rabatt på *Produkt-ID 2* i **[!UICONTROL Actions]** tabba med [!UICONTROL Priority] ange till *2*. Här antar vi att det här är en global försäljning för *Produkt-ID 2*.
1. Gå till klientsidan och lägg till *Produkt-ID 1* och *Produkt-ID 2* i kundvagnen.
1. Använd *TEST* kupongkod.

<u>Förväntade resultat</u>

* *Rabatt 1* används på *Produkt-ID 1*.
* *Rabatt 2* används på *Produkt-ID 2*.

<u>Faktiska resultat</u>

* Endast *Rabatt 1* används på *Produkt-ID 1*.
* *Rabatt 2* används inte för *Produkt-ID 2*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
