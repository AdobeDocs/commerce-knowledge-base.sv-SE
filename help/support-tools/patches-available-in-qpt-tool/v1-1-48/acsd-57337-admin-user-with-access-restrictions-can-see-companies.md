---
title: "ACSD-57337: Administratörsanvändare med åtkomstbegränsningar kan visa alla företag i rutnätet *Companies*"
description: Använd patchen ACSD-57337 för att åtgärda Adobe Commerce-problemet där en administratörsanvändare med åtkomstbegränsningar för specifika webbplatser kan visa företag från alla webbplatser i rutnätet *Companies*.
feature: Companies, B2B, Configuration
role: Admin, Developer
source-git-commit: a02c80006f1c8a434fe17322f0c6cee25f086396
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-57337: Administratörsanvändare med åtkomstbegränsningar kan visa alla företag i *Företag* rutnät

Korrigeringen ACSD-57337 åtgärdar ett problem där en administratörsanvändare med åtkomstbegränsningar för specifika webbplatser kan visa företag från alla webbplatser på *Företag* rutnät. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 är installerat. Korrigerings-ID är ACSD-57337. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En administratörsanvändare med åtkomstbegränsningar för specifika webbplatser kan visa företag från alla webbplatser i *Företag* rutnät.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en webbplats, lagra och förvara.
1. Skapa några företag som har tilldelats olika webbplatser.
1. Skapa en administratörsanvändarroll och ange rollomfånget till den skapade webbplatsen.
1. Skapa en administratör och tilldela den till den skapade rollen.
1. Logga in med en ny administratör.
1. Öppna **[!UICONTROL Customers]** > **[!UICONTROL Companies]** och observera listan över företag.

<u>Förväntade resultat</u>:

De företag som har tilldelats den extra webbplatsen visas i *Företag* rutnät.

<u>Faktiska resultat</u>:

Alla företag är synliga i *Företag* rutnät.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.