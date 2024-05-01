---
title: 'ACSD-55628: Överför fil i registreringsformulär; ersätter fil för kundattribut i butiken'
description: Använd patchen ACSD-55628 för att åtgärda Adobe Commerce-problemet genom att ladda upp en fil i registreringsformuläret och ersätta en fil för ett kundattribut i butiken.
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
exl-id: ca85b459-f72b-4663-85af-1f793935fe7e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-55628: Överför fil i företagsregistreringsformulär; ersätter fil för kundattribut i butiken

>[!NOTE]
>
>Den här korrigeringen ersätter [ACSD-51240](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md).

Korrigeringen ACSD-55628 åtgärdar problemet med att överföra en fil till företagsregistreringsformuläret och ersätta en fil för ett kundattribut i butiken. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 är installerat. Korrigerings-ID är ACSD-55628. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2 &lt; 2.4.5 och 2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att ersätta en fil för ett kundattribut i butiken.

<u>Steg som ska återskapas</u>:

1. Skapa ett nytt kundattribut med följande värden:

   * *[!UICONTROL Input Type]*: *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]*: *Ja*
   * *[!UICONTROL Forms to Use In]*: *alla tillgängliga alternativ*

1. Logga in som kund i butiken och öppna **[!UICONTROL My Account]** > **[!UICONTROL Account Information]**.
1. Ladda upp en ny bild och spara.
1. Uppdatera sidan. Ta bort den gamla bilden och överför en ny. Spara ändringarna.

<u>Förväntade resultat</u>:

Den nya bilden sparas.

<u>Faktiska resultat</u>:

Den gamla bilden visas fortfarande.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
