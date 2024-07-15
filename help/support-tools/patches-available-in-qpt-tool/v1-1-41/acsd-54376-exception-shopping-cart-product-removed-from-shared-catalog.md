---
title: 'ACSD-54376: Undantag i kundvagnen när produkten togs bort från [!UICONTROL shared catalog]'
description: Använd korrigeringsfilen ACSD-54376 för att korrigera Adobe Commerce-problemet där ett undantag inträffar i kundvagnen när en produkt tas bort från [!UICONTROL shared catalog] efter att ha lagts till i kundvagnen.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: a1e5c084-532f-49e8-ab87-6674b44218e8
source-git-commit: 1cc565d5888e5a380c04879d9aced2c19e92c2e5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54376: Undantag i kundvagnen när produkten togs bort från [!UICONTROL shared catalog]

Korrigeringen ACSD-54376 åtgärdar ett problem där ett undantag inträffar i kundvagnen när en produkt tas bort från [!UICONTROL shared catalog] efter att ha lagts till i kundvagnen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 har installerats. Korrigerings-ID är ACSD-54376. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett undantag inträffar i kundvagnen när en produkt tas bort från [!UICONTROL shared catalog] efter att ha lagts till i vagnen.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce med B2B.
1. Aktivera [!UICONTROL shared catalog].
1. Skapa en produkt och tilldela den till standardvärdet [!UICONTROL shared catalog].
1. Lägg en produkt i kundvagnen från butiken.
1. Ta bort produkten från [!UICONTROL shared catalog].
1. Navigera till utcheckningssidan med hjälp av minikundvagnslistrutan.

<u>Förväntade resultat</u>:

Undantag hanteras och visas inte för dig.

<u>Faktiska resultat</u>:

Ett ohanterat undantag visas på utcheckningssidan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
