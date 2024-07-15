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

# ACSD-53176: Produktregeln med villkoret `is one of` matchar inte

Korrigeringen ACSD-53176 åtgärdar ett problem där villkoret `is one of` för den relaterade produktregeln inte fungerar som det ska för **Produkter att matcha**. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.36 har installerats. Korrigerings-ID är ACSD-53176. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Villkoret för den relaterade produktregeln `is one of` fungerar inte korrekt för **Produkter att matcha**.

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

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
