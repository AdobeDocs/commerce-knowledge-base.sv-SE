---
title: 'ACSD-51114: Slumpmässiga produkter försvinner från stora kataloger när asynkron indexering är aktiverat'
description: Använd patchen ACSD-51114 för att åtgärda problemet med slumpmässiga Adobe Commerce-produkter som försvinner från stora kataloger när asynkron indexering är aktiverat.
exl-id: 6ea7de32-1d30-4c4a-af6e-6a0931396846
feature: Catalog Management, Categories, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51114: Slumpmässiga produkter försvinner från stora kataloger när asynkron indexering är aktiverat

>[!NOTE]
>
>Den här korrigeringen är föråldrad.

Korrigeringen ACSD-51114 åtgärdar problemet att Slumpmässiga produkter försvinner från stora kataloger när asynkron indexering är aktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 har installerats. Korrigerings-ID är ACSD-5114. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]:Sök efter korrigeringssidor].Använd patch-ID som söknyckelord för att hitta korrigeringen.

## Problem

Slumpmässiga produkter försvinner från stora kataloger när asynkron indexering är aktiverat.

<u>Steg som ska återskapas</u>:

1. Skapa en uppsättning med tio produkter.
1. Ställ in alla indexerare till läget **[!UICONTROL Update on Save]**.
1. Skapa en kategori och tilldela alla produkter till den.
1. Inaktivera alla produkter.
1. Öppna kategorin och kontrollera att det inte finns några produkter där.
1. Ställ in alla indexerare till läget **[!UICONTROL Update on Schedule]**.
1. Ange `DEFAULT_BATCH_SIZE` till 2 i `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. Aktivera produkter i följande ordning: 1, 9, 2, 5, 10, 3.
1. Kör cron, kommando.
1. Öppna kategorin igen.

<u>Förväntade resultat</u>:

Alla aktiverade produkter visas.

<u>Faktiska resultat</u>:

Alla aktiverade produkter visas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
