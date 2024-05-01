---
title: 'ACSD-49849: Kundens e-postadress har ersatts med PayPal-e-post'
description: Använd patchen ACSD-49849 för att åtgärda Adobe Commerce-problemet där kundens e-post ersattes med PayPal-e-post när en beställning gjordes med PayPal Express via GraphQL.
exl-id: 826ea90a-ac10-43e8-aa88-bd69b152ded8
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-49849: Kundens e-postadress har ersatts med [!DNL PayPal] e-post

Korrigeringen ACSD-49849 åtgärdar ett problem där en kunds e-post ersätts med en [!DNL PayPal's] e-post när du beställer med [!DNL PayPal Express] via GraphQL. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 är installerat. Korrigerings-ID är ACSD-49849. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En kunds e-postadress ersätts med en [!DNL PayPal's] e-post när du beställer med [!DNL PayPal Express] via GraphQL.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Aktivera och konfigurera [!DNL PayPal Express] och ange **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** och skapa en enkel produkt.
1. Slutför utcheckningen av gästen med GraphQL. Mer information finns i [GraphQL självstudiekurs](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) i Adobe Commerce Developer Documentation.
1. Använd [!DNL PayPal Express] som betalningsmetod.
1. Observera det e-postmeddelande du använde i det steg där du [konfigurera din e-postadress för kundvagnen](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) i Adobe Commerce Developer Documentation.
1. När beställningen är genomförd går du till Adobe Commerce Admin och kontrollerar e-postmeddelandet i den ordning som har skapats.

<u>Förväntade resultat</u>:

E-postadressen är densamma som den som angavs vid utcheckningen.

<u>Faktiska resultat</u>:

E-postmeddelandet som angetts under utcheckningen åsidosätts av e-postinställningarna i [!DNL PayPal] konto.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
