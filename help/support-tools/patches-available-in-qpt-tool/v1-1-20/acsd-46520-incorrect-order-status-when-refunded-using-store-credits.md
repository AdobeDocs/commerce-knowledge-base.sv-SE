---
title: 'ACSD-46520: Felaktig orderstatus vid återbetalning med butikskrediter'
description: I den här artikeln finns en lösning på problemet där användarna får en felaktig orderstatus när de återbetalas med butikskrediter.
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520: Felaktig orderstatus vid återbetalning med butikskrediter

ACSD-46520-korrigeringen löser problemet där användarna får en felaktig orderstatus när de återbetalas med butikskrediter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 är installerat. Korrigerings-ID är ACSD-46520. Observera att problemet har åtgärdats i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 och 2.4.2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användarna får en felaktig orderstatus när de återbetalas med butikskrediter.

<u>Steg som ska återskapas</u>:

1. Skapa ett kundkonto i butiken och logga in.
1. Tilldela butikskrediter till kunden från administratören. Butikskrediterna ska omfatta hela ordern.
1. Gör en beställning med hjälp av butikskrediterna.
1. Fakturera ordern.
1. Skapa en kreditnota för att återbetala hela orderbeloppet.
Välj **[!UICONTROL Refund to store credit]** kryssrutan.
1. Kontrollera orderstatus.

<u>Förväntade resultat</u>:

Orderstatusen är *Stängd*.

<u>Faktiska resultat</u>:

Orderstatusen är *Complete*, vilket inte har rätt status.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Adobe Commerce eller [!DNL Magento Open Source] Lokalt: [Verktyg för kvalitetspatchar > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden för verktyget Kvalitetspatchar.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i guiden för verktyget Kvalitetspatchar.
