---
title: 'ACSD-50345: reCAPTCHA-problem under utcheckningen'
description: Använd patchen ACSD-50345 för att åtgärda Adobe Commerce-problemet där reCAPTCHA v2- och v3-valideringarna misslyckas vid beställningar och vid utcheckningen.
exl-id: ac8c8130-0e4d-4610-9a55-afa779cce7a0
feature: Checkout, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-50345: reCAPTCHA-problem under utcheckningen

Korrigeringen ACSD-50345 åtgärdar ett problem där valideringarna reCAPTCHA v2 och v3 misslyckas vid beställning och vid utcheckning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31 är installerat. Korrigerings-ID är ACSD-50345. Observera att problemet delvis korrigerades i Adobe Commerce 2.4.6 och att det är planerat att åtgärdas helt i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

**Fall 1**

Google reCAPTCHA v2 läses inte in igen när en misslyckad betalning har skickats.

<u>Steg som ska återskapas</u>

1. Konfigurera **[!UICONTROL Google reCAPTCHA v2]** (*Jag är ingen robot*).
1. Aktivera **[!UICONTROL reCAPTCHA]** för utcheckning.
1. Försök att lägga en order utan att klicka på **[!UICONTROL reCAPTCHA]**.
1. När användaren får felmeddelandet för den saknade reCAPTCHA (*reCAPTCHA-validering misslyckades, försök igen*), klicka på **[!UICONTROL reCAPTCHA]** och försök sedan beställa.

<u>Förväntade resultat</u>

Ordern kommer inte att placeras med felaktig reCAPTCHA.

<u>Faktiska resultat</u>

Ett fel genereras - *reCAPTCHA-validering misslyckades, försök igen* och *Ingen sådan kundvagn med ID = 4*

**Fall 2**

Google reCAPTCHA v3 Osynlig fungerar inte i kassan och beställningen kan inte placeras. `PlaceOrder` -händelsen aktiveras inte.

<u>Steg som ska återskapas</u>

1. Konfigurera **[!UICONTROL reCAPTCHA v3 Invisible]** från **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Aktivera **[!UICONTROL reCAPTCHA v3 Invisible]** för utcheckning/beställning under **[!UICONTROL Storefront]** -fliken.
1. Försök att göra en beställning med [!UICONTROL Check/Money order] betalningsmetod.

<u>Förväntade resultat</u>

Beställningen ska placeras med **[!UICONTROL reCAPTCHA]** aktiverad.

<u>Faktiska resultat</u>

När du klickat på **[!UICONTROL Place Order]** , inaktiveras det och inget händer mer.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
