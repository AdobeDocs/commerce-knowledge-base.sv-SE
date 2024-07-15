---
title: 'ACSD-50367: Kundadressexport fungerar inte med flervalsattribut'
description: Använd patchen ACSD-50367 för att åtgärda Adobe Commerce-problemet där kundadressexporten inte fungerar när ett flervalsattribut (*`Customer Address`** utan värden skapas.
exl-id: 688831d4-b49e-48fa-b4db-1328cda09a2b
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-50367: Kundadressexport fungerar inte

Korrigeringen ACSD-50367 åtgärdar ett problem där kundadressexporten inte fungerar när ett **`Customer Address`**-attribut med flera val utan värden skapas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 har installerats. Korrigerings-ID är ACSD-50367. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundadressexport fungerar inte när ett **`Customer Address`**-attribut med flera val utan värden skapas.

<u>Förutsättningar</u>:

Skapa en kund med en adress.

<u>Steg som ska återskapas</u>:

1. Skapa ett flervalsattribut för **`Customer Address`** i **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** och välj entitetstypen **`Customer Address`**.
1. Exportera kundadresserna. Du kommer att se att inget exporteras.
1. Ta bort flervalsattributet **`Customer Address`** och exportera kundadresserna igen. Den här gången genereras adressernas CSV-fil.

<u>Förväntade resultat</u>:

Kundadresserna kan exporteras som en CSV-fil när ett **`Customer Address`**-attribut med flera val skapas.

<u>Faktiska resultat</u>:

Kundadresserna kan inte exporteras som en CSV-fil när ett **`Customer Address`**-attribut med flera val skapas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
