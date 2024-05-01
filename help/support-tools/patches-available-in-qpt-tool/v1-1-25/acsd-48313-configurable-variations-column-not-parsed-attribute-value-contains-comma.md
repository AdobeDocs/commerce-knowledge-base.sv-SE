---
title: '"ACSD-48313: [!UICONTROL configurable_variations] kolumnen har inte tolkats om attributvärdet innehåller komma'
description: Använd korrigeringsfilen ACSD-48313 för att åtgärda Adobe Commerce-problemet där [!UICONTROL configurable_variations] -kolumnen tolkas inte om attributvärdet innehåller ett komma.
exl-id: 0ac3f8da-4da3-4308-bea4-98a5b6926b0d
feature: Attributes, Configuration
role: Admin
source-git-commit: 4cb43c4f16238253fc7fc75d9af9b921dfa74158
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-48313: **[!UICONTROL configurable_variations]** kolumnen har inte tolkats om attributvärdet innehåller komma

Korrigeringsfilen ACSD-48313 löser problemet där **[!UICONTROL configurable_variations]** -kolumnen tolkas inte om attributvärdet innehåller ett komma. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 är installerat. Korrigerings-ID är ACSD-48313. Versionen där problemet kommer att åtgärdas är inte tillgänglig än.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du har exporterat konfigurerbara produkter kan den resulterande filen inte importeras igen på grund av ett formateringsproblem med **[!UICONTROL configurable_variations]** -attribut. Detta inträffar när det finns attributalternativ som innehåller kommatecken.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** och skapa ett nytt attribut _Storlek_:
1. Katalogindatatyp för butiksägare: **[!UICONTROL Dropdown]**.
1. Skapa alternativ som innehåller kommatecken, t.ex.:
   * 10,2 cm
   * 15,5 cm
1. **[!UICONTROL Advanced Attribute Properties]** - Omfång: _Global_.
1. Skapa en ny konfigurerbar produkt med funktionen Skapa konfigurationer.
1. Markera attributet ovan _Storlek_ och de två alternativen som innehåller kommatecken.
1. Gå till **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** och skapa en ny Products-export (kör kranen för att starta genereringen av CSV-filen).
1. Gå till **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** och försöker importera om samma CSV-fil som skapats ovan.

<u>Förväntade resultat</u>:

Användaren bör kunna importera filen.

<u>Faktiska resultat</u>:

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
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
