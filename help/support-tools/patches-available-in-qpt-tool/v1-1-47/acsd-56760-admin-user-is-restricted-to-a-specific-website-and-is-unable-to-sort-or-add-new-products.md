---
title: 'ACSD-56760: Administratörsanvändaren är begränsad till en specifik webbplats och kan inte sortera eller lägga till nya produkter'
description: Använd patchen ACSD-56760 för att åtgärda Adobe Commerce-problemet där den administratör som är begränsad till en viss webbplats inte kan sortera eller lägga till nya produkter i en kategori om webbutiken har en egen rotkategori.
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760: Administratörsanvändaren är begränsad till en specifik webbplats och kan inte sortera eller lägga till nya produkter

Korrigeringsfilen ACSD-56760 åtgärdar ett problem där administratören som är begränsad till en viss webbplats och inte kan sortera eller lägga till nya produkter i en kategori om webbutiken har en egen rotkategori. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.47 är installerat. Korrigerings-ID är ACSD-56760. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren som är begränsad till en viss webbplats och som inte kan sortera eller lägga till nya produkter i en kategori om webbutiken har en egen rotkategori.

<u>Steg som ska återskapas</u>:

1. Skapa *2* webbplatser.
1. Skapa en **[!UICONTROL restricted admin user]** med tillgång endast till *1* webbplats.
1. Logga in som **[!UICONTROL restricted admin user]** och försök ändra produktpositionerna i en kategori.

*Fall 1*:

* *2* butiker.
* *2* rotkategorier, alla webbplatser som är tilldelade till deras egna kategorirot.

*Fall 2*:

* *2* butiker.
* Endast *1* rotkategorin är tilldelad till båda webbplatserna.

<u>Förväntade resultat</u>:

* *Fall 1*: Den begränsade administratören ska kunna sortera produkter i den tillgängliga kategorin.
* *Fall 2*: Den begränsade administratören kan inte sortera produkter i den tillgängliga kategorin eftersom detta även påverkar den begränsade butiken.

<u>Faktiska resultat</u>:

* *Fall 1*: Den begränsade administratören kan inte sortera produkter i den tillgängliga kategorin.
* *Fall 2*: Den begränsade administratören kan sortera produkter i den tillgängliga kategorin, vilket påverkar de begränsade butikerna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
