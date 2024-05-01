---
title: '"ACSD-46767: [!UICONTROL Category] sidan caches invalidisate when the stock quantity changes'''
description: Använd korrigeringsfilen ACSD-46767 för att åtgärda Adobe Commerce-problemet där [!UICONTROL Category] sidcachen blir ogiltig när lagerkvantiteten ändras, även om produkten fortfarande finns i lager.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 39811c03-8518-4975-a128-31537b4706c0
source-git-commit: b7e2ff7cd259963adb9a113eb8e94acdaa45ba1e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category] sidan caches invalidisate when the stock quantity changes

Korrigeringen ACSD-46767 åtgärdar ett problem där [!UICONTROL Category] sidcachen blir ogiltig när lagerkvantiteten ändras, även om produkten fortfarande finns i lager. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 är installerat. Korrigerings-ID är ACSD-46767. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL Category] sidcachen blir ogiltig när lagerkvantiteten ändras.

<u>Steg som ska återskapas</u>:

1. Skapa några produkter och lägg till dem i samma kategori.
1. Öppna *[!UICONTROL Category]* på butiken för att säkerställa att sidan cachelagras.
1. Lägg beställningen på en av produkterna i kategorin *(produktkvantiteten ändras, men produkten finns fortfarande i lager)*.
1. Öppna [!UICONTROL Category] igen.

<u>Faktiska resultat</u>:

Sidan läses inte in från cachen. Den återskapas.

<u>Förväntade resultat</u>:

Sidan läses in från cachen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
