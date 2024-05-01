---
title: '''ACSD-54989: Företagsadministratören kan inte beställa när [!UICONTROL Enable Purchase Orders] inställd på Ja och [!UICONTROL Purchase Order] inställd på Nej'
description: Använd patchen ACSD-54989 för att åtgärda Adobe Commerce-problemet där företagsadministratören inte kan göra beställningar om [!UICONTROL Enable Purchase Orders] är inställt på Ja och [!UICONTROL Purchase Order] är inställd på Nej.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: c2850409-d310-4681-80ec-af8ba347854c
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54989: Företagsadministratören kan inte beställa när *[!UICONTROL Enable Purchase Orders]* ange till *Ja* och *[!UICONTROL Purchase Order]* ange till *Nej*

Korrigeringen ACSD-54989 åtgärdar ett problem där beställningar inte kan göras om **[!UICONTROL Enable Purchase Orders]** ange till *Ja* och **[!UICONTROL Purchase Order]** ange till *Nej*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 är installerat. Korrigerings-ID är ACSD-54989. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Företagsadministratörer kan inte göra beställningar när **[!UICONTROL Enable Purchase Orders]** är inställd på *Ja* och **Inköpsorder** ange till *Nej*.

<u>Förutsättningar</u>:

Installera [!DNL B2B] moduler.

<u>Steg som ska återskapas</u>:

1. Aktivera företag och lämna [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *Nej*.
1. Skapa en enkel produkt till priset 100.
1. Skapa ett nytt företag via Admin.
1. Ange [!UICONTROL **Aktivera inköpsorder**] till *Ja*.
1. Logga in som företagsadministratör i butiken.
1. Lägg den skapade enkla produkten i kundvagnen.
1. Gå till utcheckningssidan och klicka på **[!UICONTROL Place Order]** för att slutföra köpet.

<u>Förväntade resultat</u>:

Du kan göra en beställning.

<u>Faktiska resultat</u>:

The **[!UICONTROL My Account]** öppnas sidan och ordningen placeras inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
