---
title: 'ACSD-51574: Bilden har inte uppdaterats på klientsidan när den ersatts med en annan bild'
description: Använd korrigeringsfilen ACSD-51574 för att korrigera Adobe Commerce-problemet där bilden inte uppdateras på klientsidan efter att den har ersatts med en annan bild.
feature: Configuration
role: Admin
exl-id: a6f26126-71c3-43c2-bba4-60a914d7ec11
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-51574: Bilden har inte uppdaterats på klientsidan när den ersatts med en annan bild

Korrigeringen ACSD-51574 åtgärdar ett problem där bilden inte uppdateras på klientsidan efter att den har ersatts med en annan bild. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.37 har installerats. Korrigerings-ID är ACSD-51574. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Bilden uppdateras inte på förgrunden när den har ersatts med en annan bild.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt med några bilder.
1. Redigera produkten och överför en bild med ett känt namn (Exempel: *image.jpg*).
1. Spara produkten.
1. Redigera produkten igen, ta bort den gamla versionen av bilden och överför den nya versionen av bilden med samma namn. **Se till att den nya versionen är synlig och annorlunda för att se problemet.**
1. Spara produkten. Bilderna visas både i admin och front.
1. Redigera produkten igen och överför samma nya bild igen (med samma namn).
1. Spara produkten och kontrollera produktsidan i förgrunden.

<u>Förväntade resultat</u>:

Den bild som överfördes den andra gången bör vara den nya bilden, tillsammans med bildens nya namn.

<u>Faktiska resultat</u>:

Den bild som överfördes den andra gången är den tidigare borttagna äldre versionen av bilden, i stället för samma nya bild.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
