---
title: 'ACSD-50116: En administratörsanvändare kan inte skapa en URL-omskrivning för underkategorierna på nivå tre eller lägre'
description: Använd patchen ACSD-50116 för att åtgärda Adobe Commerce-problemet där en administratörsanvändare inte kan skapa en URL-omskrivning för underkategorierna nivå tre eller lägre.
exl-id: 3fa8ebc1-b55d-437e-9dc7-bf6c300b9bbe
feature: Admin Workspace, Categories
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-50116: En administratörsanvändare kan inte skapa en URL-omskrivning för underkategorierna på nivå tre eller lägre

Korrigeringen ACSD-50116 åtgärdar ett problem där en administratörsanvändare inte kan skapa en URL-omskrivning för underkategorierna på nivå tre eller lägre. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 är installerat. Korrigerings-ID är ACSD-50116. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En administratörsanvändare kan inte skapa en URL-omskrivning för underkategorierna nivå tre eller lägre.

<u>Steg som ska återskapas</u>:

1. Skapa ett kategoriträd som har fler än tre nivåer av underkategorier.
1. Försök att skapa en *[!UICONTROL URL Rewrite]* för nivå fyra-kategorin med båda *[!UICONTROL For Product]* och *[!UICONTROL For Category]* alternativ.

<u>Förväntade resultat</u>:

Kategoriträdet visar underkategorierna upp till nivå fyra eller lägre.

<u>Faktiska resultat</u>:

Kategoriträdet visar endast upp till nivå tre underkategorier.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
