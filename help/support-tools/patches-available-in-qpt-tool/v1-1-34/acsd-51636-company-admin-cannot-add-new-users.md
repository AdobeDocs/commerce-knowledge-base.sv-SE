---
title: "ACSD-51636: Företagsadministratören kan inte lägga till nya användare från kundkontoavsnittet"
description: Använd korrigeringsfilen ACSD-51636 för att åtgärda Adobe Commerce-problemet där företagsadministratören inte kan lägga till nya användare från kundkontoavsnittet trots att de har alla nödvändiga roller och behörigheter.
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 78395584-e5d3-414e-859d-a68ce1af5af1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51636: Företagsadministratören kan inte lägga till nya användare från kundkontoavsnittet

Korrigeringen ACSD-51636 åtgärdar ett problem där företagsadministratören inte kan lägga till nya användare från kundkontoavsnittet trots att de har alla nödvändiga roller och behörigheter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 är installerat. Korrigerings-ID är ACSD-51636. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Företagsadministratören kan inte lägga till nya användare från kundkontoavsnittet trots att de har alla nödvändiga roller och behörigheter.

Förutsättningar:

* B2B-modulen är installerad.
* Företagsfunktioner är aktiverade.

<u>Steg som ska återskapas</u>:

1. Skapa ett nytt företag.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Redigera **[!UICONTROL Company Admin]** skriv till *Kund*.
1. Logga in som kund.
1. Gå till **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]** och lägga till information för användaren och göra den aktiv.
1. Spara den nya användaren.

<u>Förväntade resultat</u>

Administratörsanvändaren kan lägga till en ny användare.

<u>Faktiska resultat</u>

* Administratörsanvändaren får ett felmeddelande: *Något gick fel*.
* Administratörsanvändaren kan inte skapa en ny kund.
* Loggen innehåller följande fel:

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool] guide.
