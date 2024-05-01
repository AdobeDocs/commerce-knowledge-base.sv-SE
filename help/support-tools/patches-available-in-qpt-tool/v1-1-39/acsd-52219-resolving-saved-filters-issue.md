---
title: 'ACSD-52219: Löser problem med administratörsstödraster vid växling av bokmärkesvy'
description: Använd korrigeringsfilen ACSD-52219 för att åtgärda Adobe Commerce-problemet där administratörsrutnätets sparade filter inte fungerar som förväntat när du ofta växlar mellan olika bokmärkesvyer.
feature: Admin Workspace
role: Admin
exl-id: e8333ee7-28a8-4457-aeff-6828f8ca9412
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-52219: Löser problem med administratörsstödrasterfilter vid växling av bokmärkesvy

Korrigeringen ACSD-52219 åtgärdar ett problem där administratörsrutnätets sparade filter inte fungerar som väntat när du ofta växlar mellan olika bokmärkesvyer. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 är installerat. Korrigerings-ID är ACSD-52219. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du ofta växlar mellan olika bokmärkesvyer fungerar inte de sparade filtren i administratörsrutnät som de ska.

<u>Steg som ska återskapas</u>:

1. Öppna [!DNL Sales Order] i Admin.
1. Skapa två till tre filter.
1. Kontrollera filterinställningarna genom att växla vyer för att säkerställa att de sparas korrekt.
1. Gå till Filter1 eller Filter2.
1. Uppdatera sidan för att uppdatera de data som visas.
1. Växla till en annan vy och lägg märke till att filtren inte ändras.
1. Observera att standardvyn nu visar filtrerade resultat, även om inget specifikt filter har angetts för den.

<u>Förväntade resultat</u>:

Filtren ändras inte och deras ursprungliga läge bevaras inte.

<u>Faktiska resultat</u>:

När du ändrar en vy blandas filtren ihop och rätt vy sparas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
