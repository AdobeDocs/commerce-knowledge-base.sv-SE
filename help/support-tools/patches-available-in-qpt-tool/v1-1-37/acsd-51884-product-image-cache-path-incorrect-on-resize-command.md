---
title: 'ACSD-51884: Produktbildens cachesökväg är felaktig vid storleksändring, kommando'
description: Använd korrigeringsfilen ACSD-51884 för att åtgärda Adobe Commerce-problemet där sökvägen till produktbildens cacheminne blir felaktig efter att du har kört storlekskommandot.
feature: Products
role: Admin
exl-id: cf542c4b-07b1-4f05-95bc-82bc098bcd4d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-51884: Sökvägen till produktbildens cache är felaktig vid storleksändring, kommando

Korrigeringen ACSD-51884 åtgärdar ett problem där ett internt fel där produktbildens cachesökväg blir felaktig efter att kommandot resize körts. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.37 är installerat. Korrigerings-ID är ACSD-51884. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7-2.4.7

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sökvägen till produktbildens cache blir felaktig vid storleksändring.

<u>Steg som ska återskapas</u>:

1. Skapa ny webbplats/butik/butiksgranskning.
1. Skapa en produkt och tilldela den till båda webbplatserna och överför produktbilden.
1. Skapa ett nytt tema (se Adobe.zip).
1. I `app/design/Adobe/theme/etc/view.xml` ändring:

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

till

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. Använd temat för den tidigare skapade granskningen.
1. Kontrollera produktsidan på den andra webbplatsen. Produktbilden visas korrekt.
1. Använd tömningscache:
   `bin/magento cache:flush`
1. Kontrollera produktsidan på den andra webbplatsen.

<u>Förväntade resultat</u>:

Produktbilden visas korrekt.

<u>Faktiska resultat</u>:

Produktavbildningen finns inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
