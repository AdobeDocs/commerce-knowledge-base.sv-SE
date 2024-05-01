---
title: 'ACSD-49737: Kupongen är felaktigt markerad som använd efter en misslyckad kortbetalning'
description: Använd patchen ACSD-49737 för att åtgärda Adobe Commerce-problemet där kupongen felaktigt markerats som använd efter en misslyckad kortbetalning.
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737: Kupongen är felaktigt markerad som *används* efter en misslyckad kortbetalning

Korrigeringsfilen ACSD-49737 åtgärdar ett problem där kupongen felaktigt markerats som *används* efter en misslyckad kortbetalning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 är installerat. Korrigerings-ID är ACSD-49737. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kupongen är felaktigt markerad som *används* efter en misslyckad kortbetalning.

<u>Förutsättningar</u>:

1. Konfigurera **[!UICONTROL Braintree sandbox payment]** -metod.
1. Se till att [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) konsumenten är konfigurerad och igång.

<u>Steg som ska återskapas</u>:

1. Skapa en **[!UICONTROL Cart Price Rule]** med automatiskt genererade kupongkoder.
1. Logga in som kund.
1. Lägg produkter i kundvagnen.
1. Använd en automatiskt genererad kupongkod.
1. Försök att göra en beställning med en misslyckad betalning.
1. Kontrollera kuponganvändningen i **[!UICONTROL Cart Price Rule]** under **[!UICONTROL Manage Coupon Codes]** -fliken.

<u>Förväntade resultat</u>:

Kupongen ska inte flaggas som *används* om betalningen misslyckas.

<u>Faktiska resultat</u>:

* Kupongkoden säger - Används: *Ja*, Använda tider: *1*
* Kupongkoden får användas endast en gång.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Ytterligare steg krävs efter installationen av korrigeringsfilen

(Det här avsnittet är valfritt. Det kan finnas åtgärder som krävs efter att du har implementerat korrigeringen för att åtgärda problemet.) 

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
