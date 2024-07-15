---
title: 'ACSD-52815: Indatafältet för kvantitetsfält från en icke-standardkälla stöder endast upp till 6 siffror'
description: Använd patchen ACSD-52815 för att åtgärda prestandaproblemet i Adobe Commerce där indatafältet för kvantitetsfältet för en icke-standardkälla endast stöder upp till 6 siffror, till skillnad från 8 för standardlager.
feature: Inventory, Products
role: Admin
exl-id: 44fda5ef-cb8a-481a-9112-f36d886ae3db
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52815: Indatafältet för kvantitetsfält för icke-standardkälla stöder endast upp till 6 siffror

Korrigeringen ACSD-52815 åtgärdar ett problem där indatafältet för kvantitetsfältet för en icke-standardkälla endast stöder upp till 6 siffror, till skillnad från 8 för ett standardlager. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 har installerats. Korrigerings-ID är ACSD-52815. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Indatafältet för kvantitetsfältet för en icke-standardkälla stöder endast upp till 6 siffror, till skillnad från 8 för en standardlagerkälla.

<u>Steg som ska återskapas</u>:

1. Skapa en ny aktie och källa.
1. Skapa en produkt med den nya källversionen som är inställd på 123.
1. Kontrollera den säljbara kvantiteten (123).
1. Uppdatera källkvantiteten till 12345678.
1. Kontrollera den säljbara kvantiteten igen.

<u>Förväntade resultat</u>:

Försäljningsbar kvantitet visar rätt belopp.

<u>Faktiska resultat</u>:

Den säljbara kvantiteten är 999999,9999.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
