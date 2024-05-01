---
title: "ACSD-50336: Produktvarningsmeddelanden har inte skickats"
description: Använd patchen ACSD-50336 för att åtgärda Adobe Commerce-problemet där e-postmeddelanden om produktvarningar inte skickas när en produkt finns i lager eller priset ändras.
exl-id: 0fc51603-e74d-4ce7-9e67-42826ffbfab2
feature: Communications, Personalization, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-50336: Produktvarningsmeddelanden har inte skickats

Korrigeringen ACSD-50336 åtgärdar ett problem där e-postmeddelanden om produktaviseringar inte skickas när en produkt är lagrad igen eller priset ändras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 är installerat. Korrigerings-ID är ACSD-50336. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktvarningsmeddelanden skickas inte när en produkt är tillbaka i lager eller priset ändras.

<u>Förutsättningar</u>:

Ställ in produktvarningar för när en produkt läggs till i lager igen.

<u>Steg som ska återskapas</u>:

1. Logga in som kund i butiken.
1. Öppna en produkt som inte finns i lager.
1. Prenumerera för att få ett meddelande när produkten är *tillbaka i lager*.
1. Uppdatera produkten från [!UICONTROL Admin] att _tillbaka i lager_.

<u>Förväntade resultat</u>:

Ett e-postmeddelande om att produkten *tillbaka i lager* skickas till kunden.

<u>Faktiska resultat</u>:

Kunden får inget e-postmeddelande om att produkten *tillbaka i lager*. Följande fel visas i loggen:

```
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] [] 
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
