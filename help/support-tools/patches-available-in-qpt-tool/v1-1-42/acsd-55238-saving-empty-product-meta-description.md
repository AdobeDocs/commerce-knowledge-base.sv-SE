---
title: 'ACSD-55238: Sparar den tomma metabeskrivningen för produkten'
description: Använd patchen ACSD-55238 för att åtgärda Adobe Commerce-problemet där en produktbeskrivning innehåller HTML-kod som genererats av [!DNL Page Builder] eller en annan HTML-redigerare visas alltid i metabeskrivningen och det finns inget sätt att ange att den ska vara tom.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 250026c3-925d-4a62-9855-d892c86d3d24
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-55238: Sparar den tomma produktmetabeskrivningen

Korrigeringen ACSD-55238 åtgärdar ett problem där en produktbeskrivning som innehåller HTML-kod som har genererats av en HTML-redigerare alltid visas i metabeskrivningen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 är installerat. Korrigerings-ID är ACSD-55238. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En produktbeskrivning som innehåller HTML-kod som genererats av [!DNL Page Builder] eller en annan HTML-redigerare visas alltid i metabeskrivningen och det finns inget sätt att ange att den ska vara tom.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** och skapa ett nytt block med valfritt innehåll.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** och skapa en ny produkt. Ange metabeskrivningen som tom.
1. Lägg till blocket som skapades ovan med *[!DNL Page Builder]* i *[!UICONTROL Content]* och spara produkten.
1. Öppna produkten i butiken och kontrollera dess dokumentelement `meta name = "description"`.

<u>Förväntade resultat</u>:

Metabeskrivningen är tom.

<u>Faktiska resultat</u>:

När en produkt har ett block i beskrivningen används den för produktmetabeskrivningen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
