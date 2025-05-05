---
title: 'ACSD-47336: [!UICONTROL Something went wrong]-fel vid inaktivering av meddelanden i Adobe Commerce Admin'
description: Använd ACSD-47336-korrigeringen för att åtgärda Adobe Commerce-problemet där användaren ser [!UICONTROL Something went wrong]-fel när meddelanden i  [!DNL Commerce] administratören stängs av.
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336: _[!UICONTROL Something went wrong]_-fel vid inaktivering av meddelanden i Adobe Commerce Admin

ACSD-47336-korrigeringen åtgärdar ett problem där användaren ser felet _[!UICONTROL Something went wrong]_&#x200B;när meddelanden i [!DNL Commerce]-administratören stängs av. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 har installerats. Korrigerings-ID är ACSD-47336. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder): 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren ser _[!UICONTROL Something went wrong]_-fel när meddelanden i [!DNL Commerce]-administratören stängs av.

<u>Steg som ska återskapas</u>:

1. Utför en gruppåtgärd (t.ex. satsvis uppdatering av produktattribut från produktrutnätet).
1. Slutför åtgärden (kör t.ex. `bin/magento queue:consumer:start product_action_attribute.update`).
1. Uppdatera administratörssidan för [!DNL Commerce], expandera administratörsmeddelandeavsnittet och klicka på länken **[!UICONTROL Dismiss All Completed Tasks]**.

<u>Förväntade resultat</u>:

Felet _[!UICONTROL Something went wrong]_&#x200B;ska inte visas när de slutförda aktiviteterna rensas.

<u>Faktiska resultat</u>:

Felet _[!UICONTROL Something went wrong]_&#x200B;visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
