---
title: 'ACSD-52398: Begärd kvantitet är inte tillgänglig vid försök att uppdatera kvantitet för paketerad produkt'
description: Använd patchen ACSD-52398 för att åtgärda Adobe Commerce-problemet där den begärda kvantiteten inte är tillgänglig när du försöker uppdatera kvantiteten för en paketerad produkt i kundvagnen på butiken.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 7b7f06ac-7913-4603-992a-a5620045d828
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-52398: Begärd kvantitet är inte tillgänglig vid försök att uppdatera kvantitet för paketerad produkt

Korrigeringen ACSD-52398 åtgärdar ett problem där den begärda kvantiteten inte är tillgänglig när man försöker uppdatera kvantiteten för en paketerad produkt i vagnen på butiken. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 har installerats. Korrigerings-ID är ACSD-52398. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Begärd kvantitet är inte tillgänglig när du försöker uppdatera kvantiteten för en paketerad produkt i kundvagnen i butiken.

<u>Steg som ska återskapas</u>:

1. Skapa två enkla produkter med kvantiteten *1* och *10*.
1. Skapa en paketerad produkt med de enkla produkterna.
1. Lägg den paketerade produkten i kundvagnen.
1. Redigera produkten och försök uppdatera kvantiteten till *3* för alternativet där *10* objekt är tillgängliga.

<u>Förväntade resultat</u>:

Det finns inget fel. Kvantiteten har uppdaterats eftersom det finns *10* objekt i lager för det här alternativet.

<u>Faktiska resultat</u>:

Följande fel inträffar: *Den begärda kvantiteten är inte tillgänglig*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
