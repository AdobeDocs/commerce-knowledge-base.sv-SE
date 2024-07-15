---
title: 'ACSD-52143: Anpassade alternativ tas bort efter produktimport'
description: Använd patchen ACSD-52143 för att åtgärda Adobe Commerce-problemet där anpassningsalternativen tas bort efter produktimporten.
feature: Data Import/Export
role: Admin, Developer
exl-id: 7dde1efe-37a3-443f-9ce1-82cf1b3d9da7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-52143: Anpassade alternativ tas bort efter produktimport

Korrigeringen ACSD-52143 åtgärdar ett problem där anpassade alternativ tas bort efter produktimporten. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 har installerats. Korrigerings-ID är ACSD-52143. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

De anpassade alternativen tas bort efter produktimporten.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Store]** > **[!UICONTROL All Stores]** och konfigurera en instans för flera butiker (en webbplats med två butiksvyer).
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** och skapa två produkter med [!UICONTROL Customizable Options].
1. Lägg till en [!UICONTROL Customizable Option] i varje produkt.
1. Växla till den andra butiksvyn och ändra produktnamnet för varje produkt.
1. Gå till **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** och exportera de två produkter du har skapat.
1. Hämta CSV-filen.
1. Gå till **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** och importera filen igen.
1. Kontrollera båda produkterna.

<u>Förväntade resultat</u>:

De anpassade alternativen tas inte bort efter produktimporten.

<u>Faktiska resultat</u>:

Tullalternativen tas bort efter produktimporten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
