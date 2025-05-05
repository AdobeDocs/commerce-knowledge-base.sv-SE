---
title: 'ACSD-49179: Orderrapporten visar felaktiga belopp för olika butiker.'
description: Använd patchen ACSD-49179 för att åtgärda Adobe Commerce-problemet där orderrapporten visar felaktiga belopp för olika valutor för olika butiker.
exl-id: 01e4cd2d-6c33-4cf5-bf31-bbc34eaaed1a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-49179: Orderrapport visar felaktiga belopp för olika butiker

Korrigeringen ACSD-49179 åtgärdar ett problem där orderrapporten visar felaktiga belopp för olika valutor för olika butiker. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 har installerats. Korrigerings-ID är ACSD-49179. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Orderrapporten visar felaktiga belopp för olika valutor för olika butiker.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** och ange [!UICONTROL Catalog Price Scope] = [!UICONTROL Website].
1. Skapa ytterligare en webbplats-, butik- och butiksvy.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]** och ange:
   * Standardkonfiguration:
      * Basvaluta: USD
      * Standardvisningsvaluta: USD
      * Tillåtna valutor: EUR, USD och THB (thailändska baht)
   * Huvudwebbplats:
      * Basvaluta: EUR
      * Standardvisningsvaluta: EUR
      * Tillåtna valutor: EUR
   * Ny webbplats:
      * Basvaluta: THB (thailändska baht)
      * Standardvisningsvaluta: THB (thailändska baht)
      * Tillåtna valutor: THB (Thai Baht)
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]** och ställ in tomma konverteringsgrader för THB (ange frekvenser till 1.000).
1. Skapa en produkt, tilldela den till båda webbplatserna och gör en beställning med den produkten på den nya webbplatsen som skapats tidigare.
1. Kontrollera att ordern har statusen *Bearbetar* (fakturera den).
1. Gå till **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** i backend.
1. Klicka på **[!UICONTROL Yellow]**-varningen för att uppdatera statistiken.
1. Ange rapportens omfång på den nya webbplatsen som skapats tidigare och ange filtret enligt följande:
   * [!UICONTROL Date Used]: [!UICONTROL Created]
   * [!UICONTROL Period]: [!UICONTROL Day]
   * [!UICONTROL From and To]: Samma dag som testordern placerades
   * [!UICONTROL Order Status]: [!UICONTROL Any]
   * [!UICONTROL Empty rows]: [!UICONTROL No]
   * [!UICONTROL Show Actual Values]: [!UICONTROL No]

<u>Förväntade resultat</u>:

Försäljningssumman visar det korrekta beloppet som konverterats till webbplatsens valuta.

<u>Faktiska resultat</u>:

Summan är noll.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
