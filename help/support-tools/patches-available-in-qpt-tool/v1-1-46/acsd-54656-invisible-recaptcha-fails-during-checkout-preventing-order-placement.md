---
title: Osynlig [!DNL reCAPTCHA] misslyckas under utcheckning, förhindrar att ordern läggs
description: Använd programfixen ACSD-54656 för att åtgärda Adobe Commerce-problemet där [!DNL reCAPTCHA] fungerar inte korrekt vid utcheckning, vilket förhindrar att en order placeras.
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656: Osynlig [!DNL reCAPTCHA] fungerar inte korrekt vid utcheckning, vilket förhindrar att en order placeras.

Korrigeringen ACSD-54656 åtgärdar ett problem där den osynliga [!DNL reCAPTCHA] fungerar inte korrekt vid utcheckning, vilket förhindrar att en order placeras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 är installerat. Korrigerings-ID är ACSD-54656. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Osynlig [!DNL reCAPTCHA] fungerar inte korrekt vid utcheckning, vilket förhindrar att en order placeras.

<u>Steg som ska återskapas</u>:

1. Aktivera alla typer av [!DNL reCAPTCHA] för presentkortet på [!UICONTROL Checkout] sida.
1. Lägg produkten i varukorgen och gå till **[!UICONTROL Checkout]** sida.
1. Expandera presentkortsformuläret och fyll i en giltig presentkortskupong.
1. Klicka på **[!UICONTROL See balance and apply]** -knappen.

<u>Förväntade resultat</u>:

Presentkortet har använts.

<u>Faktiska resultat</u>:

Felmeddelandet visas: *[!DNL reCAPTCHA]verifieringen misslyckades, försök igen*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
