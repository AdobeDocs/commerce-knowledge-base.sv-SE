---
title: 'ACSD-48857: Det går inte att spara ändringar efter redigering med [!DNL Page Builder]'
description: Använd korrigeringsfilen ACSD-48857 för att åtgärda Adobe Commerce-problemet där användaren inte kan spara ändringar efter redigering med [!DNL Page Builder].
exl-id: c95b354d-8954-4e9c-9e92-8a64f62f0a68
feature: Admin Workspace, CMS, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-48857: Det går inte att spara ändringar efter redigering med [!DNL Page Builder]

Korrigeringen ACSD-48857 åtgärdar ett problem där användaren inte kan spara ändringar efter redigering med [!DNL Page Builder]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 är installerat. Korrigerings-ID är ACSD-48857. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren kan inte spara ändringar efter redigering med [!DNL Page Builder].

<u>Steg som ska återskapas</u>

1. Logga in på Admin-webbplatsen.
1. Navigera till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** för att skapa en tom CMS-sida.
1. Kör det här SQL-skriptet för att ange följande **[!UICONTROL Content]** fältvärde:

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Återgå till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** i Admin.
1. Redigera sidan.
1. Gå till **[!UICONTROL Content]** -fliken.
1. Klicka på **[!UICONTROL Save]**.

<u>Förväntade resultat</u>

Sanering av innehåll i HTML implementeras. Detta tar bort [!DNL Page Builder] reserverade HTML-attribut i innehåll som genereras av textredigeraren.

<u>Faktiska resultat</u>

Sidan förblir osparad och inläsaren fortsätter snurra. Följande fel genereras i konsolen:

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
