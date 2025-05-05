---
title: 'ACSD-57588: Fel i databearbetningen av region-ID vid leverans till flera adresser'
description: Använd patchen ACSD-57588 för att åtgärda Adobe Commerce-problemet där leveransen av en order till flera adresser utlöser ett fel under bearbetningen av region-ID.
feature: Orders, Shipping/Delivery
role: Admin, Developer
source-git-commit: 1899e4601d292a8543d1c34e622251a7f6aed124
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-57588: Fel i databearbetningen av region-ID vid leverans till flera adresser

Korrigeringen ACSD-57588 åtgärdar ett problem där leverans av en order till flera adresser utlöser ett fel under bearbetning av region-ID. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 har installerats. Patch-ID:t är ACSD-57588. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel uppstod vid bearbetning av region-ID vid leverans till flera adresser.

<u>Steg som ska återskapas</u>:

1. Konfigurera betalningsmetoden [!DNL Braintree].
1. Logga in som kund i butiken.
1. Lägg en produkt i kundvagnen och fortsätt att visa och redigera kundvagnen.
1. Lägg till flera adresser *(t.ex. UK, USA, CA)* under utcheckningsprocessen och granska ordern.
1. På utcheckningssidan väljer du alternativet för kreditkortsbetalning, anger nödvändiga uppgifter och gör en beställning.

<u>Förväntade resultat</u>:

Ordern kan placeras utan fel.

<u>Faktiska resultat</u>:

Ordern är inte placerad.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
