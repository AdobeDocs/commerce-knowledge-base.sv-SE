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

Korrigeringen ACSD-50345 åtgärdar ett problem där valideringarna reCAPTCHA v2 och v3 misslyckas vid beställning och vid utcheckning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31 har installerats. Korrigerings-ID är ACSD-50345. Observera att problemet delvis korrigerades i Adobe Commerce 2.4.6 och att det är planerat att åtgärdas helt i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

**Fall 1**

Google reCAPTCHA v2 läses inte in igen när en misslyckad betalning har skickats.

<u>Steg som ska återskapas</u>

1. Konfigurera **[!UICONTROL Google reCAPTCHA v2]** (*Jag är inte en robot*).
1. Aktivera **[!UICONTROL reCAPTCHA]** för utcheckning.
1. Försök att göra en beställning utan att klicka på **[!UICONTROL reCAPTCHA]**.
1. När användaren får felmeddelandet för den saknade reCAPTCHA-valideringen (*reCAPTCHA misslyckades, försök igen*), klicka på **[!UICONTROL reCAPTCHA]** och försök sedan göra en beställning.

<u>Förväntade resultat</u>

Ordern kommer inte att placeras med felaktig reCAPTCHA.

<u>Faktiska resultat</u>

Ett fel har uppstått - *reCAPTCHA-validering misslyckades, försök igen* och *Ingen sådan kundvagn med ID = 4*

**Case #2**

Google reCAPTCHA v3 Osynlig fungerar inte i kassan och beställningen kan inte placeras. `PlaceOrder`-händelsen har inte utlösts.

<u>Steg som ska återskapas</u>

1. Konfigurera **[!UICONTROL reCAPTCHA v3 Invisible]** från **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Aktivera **[!UICONTROL reCAPTCHA v3 Invisible]** för utcheckning/placering av en order på fliken **[!UICONTROL Storefront]**.
1. Försök att göra en beställning med betalningsmetoden [!UICONTROL Check/Money order].

<u>Förväntade resultat</u>

Ordningen ska placeras med **[!UICONTROL reCAPTCHA]** aktiverat.

<u>Faktiska resultat</u>

När du har klickat på knappen **[!UICONTROL Place Order]** inaktiveras den och inget händer längre.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
