---
title: "ACSD-47179: massborttagning av produktgranskningar fungerar inte när användaren är inloggad med en begränsad användarroll"
description: Använd patchen ACSD-47179 för att åtgärda Adobe Commerce-problemet där massborttagning av produktrecensioner inte fungerar när användaren är inloggad som en begränsad användarroll.
exl-id: 85d7ce63-7dd6-4df4-b314-278d18e69fbb
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-47179: massborttagning av produktgranskningar fungerar inte när användaren är inloggad som en begränsad användarroll

Korrigeringen ACSD-47179 åtgärdar ett problem där massborttagning av produktgranskningar inte fungerar när användaren är inloggad som en begränsad användarroll. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 är installerat. Korrigerings-ID är ACSD-47179. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Massborttagning av produktgranskningar fungerar inte när du är inloggad som en begränsad användarroll.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär webbplats.
1. Skapa en användarroll som är begränsad till den sekundära webbplatsen med fullständig behörighet till följande avsnitt:
   * Katalog
   * Kund
   * Marknadsföring
1. Skapa en produkt och tilldela den till den sekundära webbplatsen.
1. Lägg till två recensioner till produkten från förgrunden.
1. Logga in på [!DNL Commerce] Administratören använder den begränsade administratörsanvändaren som just har skapats.
1. Försök att massta bort väntande granskningar.

<u>Förväntade resultat</u>:

En administratör med tillräcklig behörighet kan massta bort väntande granskningar.

<u>Faktiska resultat</u>:

Du får följande fel: _Något gick fel. Undantag genererades i support_report.log_

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
