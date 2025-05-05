---
title: 'ACSD-50234: Felaktigt kundnamn i bekräftelsemeddelande via e-post för beställningar som gjorts med  [!DNL PayPal]'
description: Använd korrigeringen ACSD-50234 för att åtgärda Adobe Commerce-problemet där kundnamnet visas felaktigt i bekräftelsemeddelandet för beställningar som gjorts med  [!DNL PayPal].
exl-id: b2e9c25a-5dd5-4b37-81e3-ca960078da77
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50234: Felaktigt kundnamn i bekräftelsemeddelande för beställningar som gjorts med [!DNL PayPal]

Korrigeringen ACSD-50234 åtgärdar ett problem där kundnamnet visas felaktigt i bekräftelsemeddelandet för beställningar som gjorts med [!DNL PayPal]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 har installerats. Korrigerings-ID är ACSD-50234. Observera att problemet har åtgärdats i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Bekräftelsemeddelande för beställningar som gjorts med [!DNL PayPal] visar fel kundnamn.

<u>Steg som ska återskapas</u>

1. Aktivera **[!UICONTROL PayPal Express Checkout]**.
1. Navigera till frontend som gäst.
1. Lägg produkter i kundvagnen.
1. Checka ut med **[!UICONTROL PayPal Express Checkout]** som betalningsmetod.
1. Kontrollera e-postmeddelandet med orderbekräftelsen.

<u>Förväntade resultat</u>

E-postmeddelandet med orderbekräftelsen, fakturameddelandet och alla leveransrelaterade e-postmeddelanden adresseras till kundens namn.

<u>Faktiska resultat</u>

E-postmeddelandet med orderbekräftelsen, fakturameddelandet och alla försändelserelaterade e-postmeddelanden adresseras till *Gäst*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
