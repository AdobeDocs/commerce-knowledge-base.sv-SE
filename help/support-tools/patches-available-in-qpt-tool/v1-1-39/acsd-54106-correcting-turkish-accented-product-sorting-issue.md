---
title: "ACSD-54106: Rectifying Turkish accented character sorting in product category"
description: Använd patchen ACSD-54106 för att åtgärda Adobe Commerce-problemet där produktsortering efter namn för turkiska accenttecken är felaktig.
feature: Categories, Products, Search
role: Admin
exl-id: 80386ded-4ada-4822-b073-f477ca123093
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-54106: Rektifiera turkiska teckensorteringar med accenttecken i produktkategorin

Korrigeringen ACSD-54106 åtgärdar ett problem där produktsortering efter namn för turkiska accenttecken är felaktig. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 är installerat. Korrigerings-ID är ACSD-54106. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sorteringen av produkter i kategorier efter namn är felaktig för turkiska accenttecken.

<u>Steg som ska återskapas</u>:

1. Logga in på adminpanelen.
1. Skapa enkla produkter med följande namn och tilldela dem till valfri kategori:

* Namn A
* Namn
* Namn D
* Ğ
* Namn M
* Namn Ö
* Namn Ü
* Namn Y
* Namn Z

1. Navigera till butiken och öppna kategorin som innehåller produkterna.
1. Ändra sorteringsordningen till *[!UICONTROL By Name]*.

<u>Förväntade resultat</u>:

Produkterna sorteras korrekt i följande ordning:

* Namn A
* Namn
* Namn D
* Ğ
* Namn M
* Namn Ö
* Namn Ü
* Namn Y
* Namn Z

<u>Faktiska resultat</u>:

Produkterna sorteras felaktigt i följande ordning:

* Namn A
* Namn D
* Namn M
* Namn Y
* Namn Z
* Namn
* Namn Ö
* Namn Ü
* Ğ

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
