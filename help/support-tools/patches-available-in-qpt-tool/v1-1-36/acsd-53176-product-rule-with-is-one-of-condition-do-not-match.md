---
title: '"ACSD-53176: Produktregeln med "är ett av"-villkor matchar inte"'
description: Använd patchen ACSD-53176 för att åtgärda Adobe Commerce-problemet där den relaterade produktregeln "är ett av"-villkor inte fungerar som den ska för "Produkter att matcha".
feature: Marketing Tools
role: Admin
exl-id: 91f05f5b-6a5e-4b93-9dfb-88cbeccb6c9e
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-53176: Produktregel med `is one of` villkoret matchar inte

Korrigeringen ACSD-53176 åtgärdar ett problem där den relaterade produktregeln `is one of` villkoret fungerar inte korrekt för **Produkter som ska matchas**. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.36 är installerat. Korrigerings-ID är ACSD-53176. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Regeln för den relaterade produkten `is one of` villkoret fungerar inte korrekt för **Produkter som ska matchas**.

<u>Steg som ska återskapas</u>:

1. Skapa 3-4 produkter.
1. Skapa en ny relaterad produktregel.

   Ställ in regeln så att den matchar två eller flera produkter:
   * `SKU is one of "S1,S2".`

   Ställ in regeln så att två eller flera objekt visas:
   * `Product SKU is one of constant value "S2,S3".`

1. Öppna S1-produkten på Storefront.

<u>Förväntade resultat</u>:

De relaterade produkterna &quot;S2&quot; och &quot;S3&quot; visas på båda produktsidorna &quot;S1&quot; och &quot;S2&quot;.

<u>Faktiska resultat</u>:

Relaterade produkter visas inte på produktsidorna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
