---
title: 'ACSD-54887: Kundvagnen raderas efter att kundsessionen har upphört'
description: Använd korrigeringsfilen ACSD-54887 för att korrigera Adobe Commerce-problemet där kundvagnen raderas efter att kundsessionen har upphört och [!UICONTROL Persistent Shopping Cart] är aktiverat.
feature: Shopping Cart
role: Admin, Developer
exl-id: 81e0a20e-0c68-420e-b14e-3f331249c8d9
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-54887: Kundvagnen raderas efter att kundsessionen har upphört

Korrigeringen ACSD-54887 åtgärdar ett problem där kundens kundvagn raderas efter att kundsessionen har upphört och [!UICONTROL Persistent Shopping Cart] är aktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 har installerats. Patch-ID:t är ACSD-54887. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p8, 2.4.5-p3 - 2.4.5-p7 och 2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundvagnen raderas när kundsessionen har gått ut med [!UICONTROL Persistent Shopping Cart] aktiverat.

<u>Steg som ska återskapas</u>:

1. Aktivera [!UICONTROL Persistent Shopping Cart]. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *Ja*.

   Logga in med Persistence aktiverat (Obs! Det är inte tillgängligt för popup-auktorisering, utan bara på den direkta [!UICONTROL Sign in]-sidan).

1. Lägg en produkt i kundvagnen.
1. Gå till kassan och välj en betalningsmetod.
1. Förfaller sessionen (ta bort `PHPSESSID`).
1. Uppdatera sidan. Observera att offerten omedelbart konverteras till en gästoffert eftersom en betalningsmetod redan har valts och cookien [!UICONTROL Persistent Cart] har tagits bort.
1. Förfaller sessionen (ta bort `PHPSESSID`).
1. Uppdatera sidan. Se till att vagnen är tom.
1. Logga in igen.

<u>Förväntade resultat</u>:

Kundvagnen har produkten när du loggar in igen.

<u>Faktiska resultat</u>:

Kundvagnen är tom när du loggar in igen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
