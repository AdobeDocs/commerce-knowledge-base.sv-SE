---
title: 'ACSD-53979: JS-fel inträffar på hemsidan'
description: Använd patchen ACSD-53979 för att åtgärda Adobe Commerce-problemet där ett JavaScript-fel inträffar på hemsidan om välkomstmeddelandet innehåller ett enkelt citat.
feature: Page Content
role: Admin, Developer
exl-id: 4e5afc5c-322f-4681-b2aa-01d93be74d4a
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-53979: JavaScript-fel inträffar på hemsidan

Korrigeringen ACSD-53979 åtgärdar ett problem där ett JavaScript-fel inträffar på hemsidan om välkomstmeddelandet innehåller ett enkelt citattecken. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 har installerats. Korrigerings-ID är ACSD-53979. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett JavaScript-fel inträffar på hemsidan om välkomstmeddelandet innehåller ett enkelt citattecken.

<u>Steg som ska återskapas</u>:

1. Ange ett välkomstmeddelande som standard i filen `en_US.csv` på [!DNL French]-språket eller skriv ett citattecken som nedan:
   `app/code/Magento/Theme/i18n/en_US.csv`

   ```CSV
       "Default welcome msg!","Message d'accueil par défaut"
   ```

1. Gå till fronten.

<u>Förväntade resultat</u>:

Sidslut laddas utan JavaScript-fel.

<u>Faktiska resultat</u>:

Ett JavaScript-fel inträffar:

```JS
    Uncaught SyntaxError: Unable to process binding "ifnot: function(){return customer().fullname }"
    Message: Unable to parse bindings.
    Bindings value: text: 'Message d'accueil par défaut'
    Message: Unexpected identifier 'accueil'
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
