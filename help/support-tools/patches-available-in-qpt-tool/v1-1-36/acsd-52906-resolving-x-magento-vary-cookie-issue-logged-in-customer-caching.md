---
title: 'ACSD-52906: Löser X-Magento-Vary-cookie-problem för inloggad kundcache'
description: Använd ACSD-52906-korrigeringen för att åtgärda Adobe Commerce-problemet där X-Magento-Vary-cookien är felaktigt inställd för inloggade kunder.
feature: Cache
role: Admin, Developer
exl-id: 863e0808-9208-467d-8d56-9dd7a7f4354d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-52906: Löser X-Magento-Vary-cookie-problem för inloggade kunder

ACSD-52906-korrigeringen åtgärdar ett problem där X-Magento-Vary-cookien inte är korrekt inställd för inloggade kunder. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.36 är installerat. Korrigerings-ID är ACSD-52906. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

X-Magento-Vary-cookie är felaktigt inställd för inloggade kunder som tillhör samma kundsegment, vilket orsakar felaktig cachelagring för vissa sidor.

<u>Förutsättningar</u>:

Adobe Commerce Inventory management-moduler (MSI) är installerade och aktiverade.

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL Varnish] eller [!DNL Fastly] cache.
1. Skapa ett nytt kundsegment och tilldela det till *Registrerad* kunder.
1. Skapa två kunder, till exempel customer1 och customer2.
1. Rensa cachen.
1. Logga in som kund1 och gå till startsidan.
1. Öppna en inkodade sida i webbläsaren.
1. Gå till en annan sida än startsidan.
1. Logga in som kund2.
1. Gå till startsidan.
1. Kontrollera om sidan är cachelagrad i webbläsarens dev-konsol.

<u>Förväntade resultat</u>:

Sidan hämtas från cachen.

<u>Faktiska resultat</u>:

Sidan är inte cachelagrad.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
