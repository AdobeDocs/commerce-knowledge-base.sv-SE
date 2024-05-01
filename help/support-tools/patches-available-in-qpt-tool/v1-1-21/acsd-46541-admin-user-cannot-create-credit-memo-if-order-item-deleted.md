---
title: "ACSD-46541: En administratörsanvändare kan inte skapa en kreditnota om ett orderobjekt tas bort"
description: Använd korrigeringsfilen ACSD-46541 för att åtgärda Adobe Commerce-problemet där du inte kan skapa en kreditnota i Adobe Commerce Admin när en produkt har tagits bort.
exl-id: ff3f8f21-76c1-41b5-bf02-349403a46fc1
feature: Admin Workspace, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46541: En administratörsanvändare kan inte skapa en kreditnota om ett orderobjekt tas bort

Korrigeringen ACSD-46541 åtgärdar ett problem där en administratörsanvändare inte kan skapa en kreditnota om ett orderobjekt tas bort. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 är installerat. Korrigerings-ID är ACSD-46541. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När en produkt har tagits bort kan du inte skapa en kreditnota i Commerce Admin.

<u>Steg som ska återskapas</u>:

1. Logga in på Commerce Admin.
1. Skapa en order.
1. Fakturera ordern.
1. Ta bort produkten från beställningen.
1. Klicka på **[!UICONTROL Credit Memo]** på orderredigeringssidan.
1. Klicka på **[!UICONTROL Refund Offline]** för att skapa en kreditnota.

<u>Förväntade resultat</u>:

En kreditnota har skapats.

<u>Faktiska resultat</u>:

The _Följande produkter med begärda SKU:er hittades inte: SKU001_ visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
