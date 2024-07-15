---
title: 'ACSD 49843: Produktnedladdningslänken är inte tillgänglig efter automatisk fakturering med [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Använd patchen ACSD-49843 för att åtgärda problemet med Adobe Commerce där produktnedladdningslänken inte är tillgänglig efter att den beställda artikeln automatiskt fakturerats av en onlinebetalningsmetod när [!UICONTROL Payment Action] är inställd på [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843: Länken för produktnedladdning är inte tillgänglig efter automatisk fakturering med [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

Korrigeringen ACSD-49843 åtgärdar ett problem där produkthämtningslänken inte är tillgänglig efter att den beställda artikeln automatiskt fakturerats av en onlinebetalningsmetod när [!UICONTROL Payment Action] är inställd på [!UICONTROL Intent Sale]. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.37 har installerats. Korrigerings-ID är ACSD-49843. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktnedladdningslänken är inte tillgänglig när den beställda artikeln automatiskt faktureras av en onlinebetalningsmetod när [!UICONTROL Payment Action] är inställd på [!UICONTROL Intent Sale].

<u>Steg som ska återskapas</u>:

1. Logga in på Adobe Commerce Admin och gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * I listrutan [!UICONTROL Payment Action] väljer du **[!UICONTROL Intent Sale]** och ställer in *[!UICONTROL Enable Card Payments]* på *Ja*.

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** och se till att det är inställt på *&quot;Fakturerat&quot;*.
1. Logga in som kund i butiken.

   * Lägg alla nedladdningsbara produkter och en enkel produkt i kundvagnen.
   * Använd [!DNL Braintree Pay] om du vill göra en beställning med hjälp av kortalternativet.

1. Gå till **[!UICONTROL My Orders]** och se att fakturan skapas automatiskt för ordern och att båda artikelstatusvärdena är *&quot;Fakturerad&quot;*.
1. Gå till **[!UICONTROL My Downloadable Products]** och observera att nedladdningslänken inte är tillgänglig än.
1. Gå till den beställningen i Admin och skapa en leverans för den.
1. Gå till **[!UICONTROL My Downloadable Products]** i butiken och observera att nedladdningslänken nu är tillgänglig.

<u>Förväntade resultat</u>:

Hämtningslänken är tillgänglig när den hämtningsbara produktstatusen är *&quot;Fakturerad&quot;*.

<u>Faktiska resultat</u>:

Hämtningslänken är inte tillgänglig även om den hämtningsbara produktstatusen är *&quot;Fakturerad&quot;*. Den är bara tillgänglig efter att en leverans har skapats för den fysiska produkten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
