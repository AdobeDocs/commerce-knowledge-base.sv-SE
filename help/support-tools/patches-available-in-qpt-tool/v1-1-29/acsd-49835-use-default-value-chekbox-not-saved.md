---
title: '"ACSD-49835: [!UICONTROL Use Default Value] kryssrutan har inte sparats'
description: Använd korrigeringsfilen ACSD-49835 för att åtgärda Adobe Commerce-problemet där [!UICONTROL Use Default Value] kryssrutan sparas inte korrekt på en arkivnivå för ett flervalsattribut.
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835: [!UICONTROL Use Default Value] kryssrutan har inte sparats

Korrigeringen ACSD-49835 åtgärdar ett problem där [!UICONTROL Use Default Value] kryssrutan sparas inte korrekt på en arkivnivå för ett flervalsattribut. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 är installerat. Korrigerings-ID är ACSD-49835. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The [!UICONTROL Use Default Value] kryssrutan sparas inte korrekt på en arkivnivå för ett flervalsattribut.

<u>Steg som ska återskapas</u>:

1. Skapa en **[!UICONTROL Multiple-select Attribute]** in **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** och lägga till det i en attributuppsättning.
1. Gå till **[!UICONTROL Product]** och spara **[!UICONTROL Values]** in **[!UICONTROL All Store Views (Default Scope)]**.
1. Gå till en specifik **[!UICONTROL Store View Scope]** och spara produkten.
1. Gå till **[!UICONTROL Store View Scope]** och kontrollera **[!UICONTROL Use Default Value]** kryssrutan.

<u>Förväntade resultat</u>:

Flervalsattributvärden sparas korrekt när du kontrollerar [!UICONTROL Use Default Value] kryssrutan i [!UICONTROL Store View Scope].

<u>Faktiska resultat</u>:

Flervalsattributvärden sparas inte korrekt vid kontroll av [!UICONTROL Use Default Value] kryssrutan i [!UICONTROL Store View Scope].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
