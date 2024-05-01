---
title: 'ACSD-54966: Korrigera för återanvändning av kupongkoder efter misslyckade beställningar'
description: Använd patchen ACSD-54966 för att åtgärda Adobe Commerce-problemet och förhindra återanvändning av kupongkoder som begränsas per kampanj och kundvagn efter en tidigare misslyckad beställning.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: 931cfe7a-30a3-4a7d-ada5-4e2d7084f3e1
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-54966: Korrigera för återanvändning av kupongkoder efter misslyckade beställningar

Korrigeringen ACSD-54966 åtgärdar ett problem som förhindrar återanvändning av kupongkoder som begränsas per kund efter en tidigare misslyckad order. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 är installerat. Korrigerings-ID är ACSD-54966. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En kupongkod som är begränsad för engångsbruk per kund kan inte återanvändas efter en tidigare misslyckad order.

<u>Steg som ska återskapas</u>:

1. Ställ in en kundvagnsprisregel med *[!UICONTROL Uses per Customer]* = *1*.
1. Fortsätt att göra ett köp med den tilldelade kupongkoden.
1. Avbryt beställningen från adminpanelen eller utför beställningen med ett betalningsfel.
1. Kör kommandot: `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Försök att lägga en efterföljande order med samma kupongkod för samma kund.

<u>Förväntade resultat</u>:

När kunden har annullerat beställningen eller påträffat ett betalningsfel kan den återanvända kupongkoden för ett nytt köp.

<u>Faktiska resultat</u>:

Kunden kan inte återanvända kupongkoden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
