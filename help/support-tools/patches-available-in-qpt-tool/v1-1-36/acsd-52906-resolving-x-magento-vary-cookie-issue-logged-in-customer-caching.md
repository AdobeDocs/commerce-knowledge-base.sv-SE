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

ACSD-52906-korrigeringen åtgärdar ett problem där X-Magento-Vary-cookien inte är korrekt inställd för inloggade kunder. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.36 har installerats. Korrigerings-ID är ACSD-52906. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

X-Magento-Vary-cookie är felaktigt inställd för inloggade kunder som tillhör samma kundsegment, vilket orsakar felaktig cachelagring för vissa sidor.

<u>Förutsättningar</u>:

Adobe Commerce Inventory management-moduler (MSI) är installerade och aktiverade.

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL Varnish] eller [!DNL Fastly]-cache.
1. Skapa ett nytt kundsegment och tilldela det till *registrerade*-kunder.
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

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
