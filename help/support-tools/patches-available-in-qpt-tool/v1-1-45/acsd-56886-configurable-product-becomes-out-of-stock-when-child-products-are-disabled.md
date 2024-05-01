---
title: 'ACSD-56886: Den konfigurerbara produkten blir inte i lager när underordnade produkter inaktiveras'
description: Använd patchen ACSD-56886 för att åtgärda Adobe Commerce-problemet där den konfigurerbara produkten blir otillgänglig när produkter inaktiveras.
feature: Products
role: Admin, Developer
exl-id: 809b9829-283f-4e3c-bf27-1944057f944f
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56886: Den konfigurerbara produkten blir inte i lager när underordnade produkter inaktiveras

Korrigeringen ACSD-56886 åtgärdar ett problem där den konfigurerbara produkten inte finns i lager när underordnade produkter inaktiveras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 är installerat. Korrigerings-ID är ACSD-56886. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den konfigurerbara produkten blir inte i lager när underordnade produkter inaktiveras.

<u>Steg som ska återskapas</u>:

1. Logga in som administratör.
1. Ange alla indexerare i dialogrutan **[!UICONTROL Update By Schedule]** läge.
1. Skapa följande konfigurerbara produkt:

   * Namn = *PROVNINGEN ÄR KONFIGURERAD 1*
   * Attribut = *färg*
   * Värden = *röd* och *svart*
   * Pris på **röd**  underordnad produkt = *100 dollar*;
   * Pris på den svarta underordnade produkten = *200 dollar*.

1. Skapa följande schemalagda uppdatering för den konfigurerbara produkten:

   * Startdatum = *3* från och med nu.
   * Slutdatum = *5* minuter efter startdatum.
   * Produktnamn = *TEST CONFIGURABLE 1 edited*.
   * Inaktivera **röd** underordnad produkt i **Konfigurerbar** -avsnitt.

1. Vänta på startdatumet.
1. Öppna den konfigurerbara produktinformationen på Storefront.

<u>Förväntade resultat</u>:

Den konfigurerbara produkten visas som **I Stock** med **Endast 200** etikett.

<u>Faktiska resultat</u>:

Den konfigurerbara produkten visas som **Slut på lager**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
