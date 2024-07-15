---
title: 'Kryssrutan ACSD-49835: [!UICONTROL Use Default Value] har inte sparats.'
description: Använd korrigeringsfilen ACSD-49835 för att åtgärda Adobe Commerce-problemet där kryssrutan [!UICONTROL Use Default Value] inte har sparats korrekt på en butiksnivå för ett flervalsattribut.
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835: Kryssrutan [!UICONTROL Use Default Value] sparas inte

Korrigeringen ACSD-49835 åtgärdar ett problem där kryssrutan [!UICONTROL Use Default Value] inte har sparats korrekt på en butiksnivå för ett flervalsattribut. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 har installerats. Korrigerings-ID är ACSD-49835. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kryssrutan [!UICONTROL Use Default Value] sparas inte korrekt på en butiksnivå för ett flervalsattribut.

<u>Steg som ska återskapas</u>:

1. Skapa en **[!UICONTROL Multiple-select Attribute]** i **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** och lägg till den i en attributuppsättning.
1. Gå till en **[!UICONTROL Product]** och spara **[!UICONTROL Values]** i **[!UICONTROL All Store Views (Default Scope)]**.
1. Gå till en specifik **[!UICONTROL Store View Scope]** och spara produkten.
1. Gå till **[!UICONTROL Store View Scope]** och markera kryssrutan **[!UICONTROL Use Default Value]**.

<u>Förväntade resultat</u>:

Flervalsattributvärden sparas korrekt när kryssrutan [!UICONTROL Use Default Value] i [!UICONTROL Store View Scope] markeras.

<u>Faktiska resultat</u>:

Flervalsattributvärden sparas inte korrekt när kryssrutan [!UICONTROL Use Default Value] i [!UICONTROL Store View Scope] markeras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
