---
title: 'ACSD 49843: Länken för nedladdning av produkter är inte tillgänglig efter automatisk fakturering med [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Använd korrigeringsfilen ACSD-49843 för att åtgärda problemet med Adobe Commerce-problem där nedladdningslänken inte är tillgänglig när den beställda artikeln automatiskt faktureras via en onlinebetalningsmetod när [!UICONTROL Payment Action] är inställd på [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843: Länken för nedladdning av produkter är inte tillgänglig efter att ha fakturerats automatiskt med [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

Korrigeringen ACSD-49843 åtgärdar ett problem där produktnedladdningslänken inte är tillgänglig efter att den beställda artikeln automatiskt fakturerats via en onlinebetalningsmetod när [!UICONTROL Payment Action] är inställd på [!UICONTROL Intent Sale]. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.37 är installerat. Korrigerings-ID är ACSD-49843. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktnedladdningslänken är inte tillgänglig efter att den beställda artikeln automatiskt fakturerats av en onlinebetalningsmetod när [!UICONTROL Payment Action] är inställd på [!UICONTROL Intent Sale].

<u>Steg som ska återskapas</u>:

1. Logga in på Adobe Commerce Admin och gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * I [!UICONTROL Payment Action] nedrullningsbar meny, välja **[!UICONTROL Intent Sale]** och ange *[!UICONTROL Enable Card Payments]* till *Ja*.

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** och se till att den är inställd på *&quot;Fakturerat&quot;*.
1. Logga in som kund i butiken.

   * Lägg alla nedladdningsbara produkter och en enkel produkt i kundvagnen.
   * Använd [!DNL Braintree Pay] om du vill beställa med hjälp av kortalternativet.

1. Gå till **[!UICONTROL My Orders]** och se till att fakturan skapas automatiskt för ordern och att båda artikelstatusvärdena är *&quot;Fakturerat&quot;*.
1. Gå till **[!UICONTROL My Downloadable Products]** och observera att nedladdningslänken inte är tillgänglig än.
1. Gå till den beställningen i Admin och skapa en leverans för den.
1. Gå till butiken **[!UICONTROL My Downloadable Products]** och observera att nedladdningslänken nu är tillgänglig.

<u>Förväntade resultat</u>:

Hämtningslänken är tillgänglig när den hämtningsbara produktens status är *&quot;Fakturerat&quot;*.

<u>Faktiska resultat</u>:

Hämtningslänken är inte tillgänglig även om den hämtningsbara produktstatusen säger *&quot;Fakturerat&quot;*. Den är bara tillgänglig efter att en leverans har skapats för den fysiska produkten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
