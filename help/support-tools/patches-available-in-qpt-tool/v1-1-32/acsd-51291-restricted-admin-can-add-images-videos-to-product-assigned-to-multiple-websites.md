---
title: 'ACSD-51291: Begränsad administratör kan lägga till bilder/videor till produkt som tilldelats flera webbplatser'
description: Använd patchen ACSD-51291 för att åtgärda Adobe Commerce-problemet där en begränsad administratör med tillgång till en webbplats kan lägga till bilder/videor till en produkt som tilldelats flera webbplatser.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: d3cf5009-6b80-4841-95c3-75bb15c9c0a4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# ACSD-51291: Begränsad administratör kan lägga till bilder/videor till produkter som tilldelats flera webbplatser

Korrigeringen ACSD-51291 åtgärdar ett problem där en begränsad administratör med tillgång till en webbplats kan lägga till bilder/videor till en produkt som tilldelats flera webbplatser. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 är installerat. Korrigerings-ID är ACSD-51291. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En begränsad administratör med tillgång till en webbplats kan lägga till bilder/videor till en produkt som tilldelats flera webbplatser.

<u>Steg som ska återskapas</u>

1. Logga in som administratör.
1. Skapa en andra webbplats-, butiks- och butiksvy.
1. Skapa en andra administratörsroll med resurser endast för den andra webbplatsen, butiken och butiksvyn.
1. Skapa en andra administratör och tilldela den till den nya begränsade administratörsrollen.
1. Skapa en ny produkt och tilldela den till både standardwebbplatsen och de nya webbplatserna.
1. Logga ut från huvudadministratörsprofilen.
1. Logga in som ny begränsad administratör.
1. Redigera den skapade produkten som har tilldelats båda webbplatserna.
1. Öppna **[!UICONTROL Images and Videos]** -fliken.

<u>Förväntade resultat</u>:

* Följande meddelande visas:

  *Begränsad administratör får endast utföra åtgärder med bilder eller videoklipp när administratören har behörighet till alla webbplatser som produkten är tilldelad till.*

* The **[!UICONTROL Add Video]** knappen är inte aktiv.

<u>Faktiska resultat</u>:

Den begränsade administratören kan lägga till bilder och videoklipp även när produkten har tilldelats en webbplats som den inte har tillgång till.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
