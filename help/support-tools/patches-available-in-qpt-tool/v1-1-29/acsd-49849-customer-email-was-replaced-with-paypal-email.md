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

# ACSD-49849: Kundens e-postadress har ersatts med [!DNL PayPal] e-postadress

Korrigeringen ACSD-49849 åtgärdar ett problem där en kunds e-post ersätts med ett [!DNL PayPal's]-e-postmeddelande när en beställning görs med [!DNL PayPal Express] via GraphQL. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 har installerats. Korrigerings-ID är ACSD-49849. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En kunds e-postadress ersätts med ett [!DNL PayPal's]-e-postmeddelande när en beställning görs med [!DNL PayPal Express] via GraphQL.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Aktivera och konfigurera [!DNL PayPal Express] och ange **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** och skapa en enkel produkt.
1. Slutför utcheckningen av gästen med GraphQL. Mer information finns i [GraphQL självstudiekurs ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) i Adobe Commerce Developer Documentation.
1. Använd [!DNL PayPal Express] som betalningsmetod.
1. Observera det e-postmeddelande du använde i det steg där du [konfigurerade e-postmeddelandet för kundvagnen](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) i Adobe Commerce Developer Documentation.
1. När beställningen är genomförd går du till Adobe Commerce Admin och kontrollerar e-postmeddelandet i den ordning som har skapats.

<u>Förväntade resultat</u>:

E-postadressen är densamma som den som angavs vid utcheckningen.

<u>Faktiska resultat</u>:

E-postadressen som angavs vid utcheckningen åsidosätts av e-postinställningen i kontot [!DNL PayPal].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
