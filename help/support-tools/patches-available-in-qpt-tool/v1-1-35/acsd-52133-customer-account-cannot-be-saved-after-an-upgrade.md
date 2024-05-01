---
title: 'ACSD-52133: Kundkontot kan inte sparas efter en uppgradering'
description: Använd patchen ACSD-52133 för att åtgärda Adobe Commerce-problemet där ett kundkonto inte kan sparas efter en uppgradering.
feature: Customers, Upgrade
role: Admin
exl-id: 0db7c79e-10e1-4850-81b5-4812fb051941
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-52133: Kundkonto kan inte sparas efter en uppgradering

Korrigeringen ACSD-52133 åtgärdar ett problem där ett kundkonto inte kan sparas efter en uppgradering. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 är installerat. Korrigerings-ID är ACSD-52133. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att spara kundkontot efter en uppgradering.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce version 2.4.4.
1. Skapa en kund.
1. Uppgradera Adobe Commerce till 2.4.6 från den tidigare versionen av 2.4.4 där en kund redan skapats.
1. Ange krypteringsnyckeln enligt nedan `env.php`:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Ange värdena nedan i databasen för alla kunder under `customer_entity` tabell:

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Redigera kunden som ovanstående värden uppdaterades för.
1. Klicka på **[!UICONTROL Save Customer]** eller **[!UICONTROL Save and Continue Edit]**

<u>Förväntade resultat</u>:

Kunden har sparats utan fel.

<u>Faktiska resultat</u>:

* Kundposten sparas inte.
* Administratören ser följande felmeddelande: *Något gick fel när kunden sparades.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
