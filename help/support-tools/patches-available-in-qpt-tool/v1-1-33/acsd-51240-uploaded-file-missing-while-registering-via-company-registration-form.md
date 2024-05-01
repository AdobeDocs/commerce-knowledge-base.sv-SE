---
title: 'ACSD-51240: Filen saknas när du registrerar via företagsregistreringsformulär'
description: Använd patchen ACSD-51240 för att åtgärda Adobe Commerce-problemet där den överförda filen saknas när du registrerar via företagsregistreringsformuläret.
exl-id: e5822c54-4e77-46b0-84b6-5e25c3845974
source-git-commit: e1fe8936c56f422ae591c6424d8a72621093db81
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51240: Filen saknas vid registrering via företagsregistreringsformulär

>[!NOTE]
>
>Den här korrigeringen har ersatts med [ACSD-55628](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md).

Korrigeringen ACSD-51240 åtgärdar ett problem där den överförda filen saknas när den registreras via företagsregistreringsformuläret. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 är installerat. Korrigerings-ID är ACSD-51240. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Problem

Överförd fil saknas vid registrering via företagsregistreringsformulär.

<u>Steg som ska återskapas</u>:

1. Ange **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *Ja*.
1. Skapa ett nytt kundattribut för **[!UICONTROL File]** text, ange **[!UICONTROL Show in StoreFront]** = *Ja* och markera **[!UICONTROL all forms]**.
1. Skapa ett nytt företag på Storefront och överför en bild för det nya attributet.
Öppna företaget och administratörsanvändaren på Storefront.

<u>Förväntade resultat</u>:

Den överförda filen visas.

<u>Faktiska resultat</u>:

Den överförda filen visas inte på företagssidan eller på adminkundsidan i [!UICONTROL Commerce Admin].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
