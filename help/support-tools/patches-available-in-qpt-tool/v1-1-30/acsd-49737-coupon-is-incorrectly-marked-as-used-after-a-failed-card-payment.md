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

# ACSD-49737: Kupongen är felaktigt markerad som *använd* efter en misslyckad kortbetalning

Korrigeringen ACSD-49737 åtgärdar ett problem där kupongen felaktigt markerats som *använd* efter en misslyckad kortbetalning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 har installerats. Korrigerings-ID är ACSD-49737. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kupongen är felaktigt markerad som *använd* efter en misslyckad kortbetalning.

<u>Förutsättningar</u>:

1. Konfigurera metoden **[!UICONTROL Braintree sandbox payment]**.
1. Kontrollera att konsumenten [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) har konfigurerats och körs.

<u>Steg som ska återskapas</u>:

1. Skapa en **[!UICONTROL Cart Price Rule]** med automatiskt genererade kupongkoder.
1. Logga in som kund.
1. Lägg produkter i kundvagnen.
1. Använd en automatiskt genererad kupongkod.
1. Försök att göra en beställning med en misslyckad betalning.
1. Kontrollera kuponganvändningen i **[!UICONTROL Cart Price Rule]** under fliken **[!UICONTROL Manage Coupon Codes]**.

<u>Förväntade resultat</u>:

Kupongen ska inte flaggas som *använd* om betalningen misslyckas.

<u>Faktiska resultat</u>:

* Kupongkoden säger - Används: *Ja*, Används i tider: *1*
* Kupongkoden får användas endast en gång.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Ytterligare steg krävs efter installationen av korrigeringsfilen

(Det här avsnittet är valfritt. Det kan finnas åtgärder som krävs efter att du har implementerat korrigeringen för att åtgärda problemet.) 

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
