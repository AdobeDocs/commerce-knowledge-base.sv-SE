---
title: Osynlig [!DNL reCAPTCHA] misslyckas under utcheckning, vilket förhindrar att ordern placeras
description: Använd ACSD-54656-korrigeringen för att åtgärda Adobe Commerce-problemet där den osynliga [!DNL reCAPTCHA]  inte fungerar som den ska vid utcheckning, vilket förhindrar att en order läggs.
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656: Osynlig [!DNL reCAPTCHA] fungerar inte korrekt vid utcheckning, vilket förhindrar att en order placeras.

ACSD-54656-korrigeringen åtgärdar ett fel där den osynliga [!DNL reCAPTCHA] inte fungerar korrekt under utcheckning, vilket förhindrar att en order placeras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 har installerats. Korrigerings-ID är ACSD-54656. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Osynlig [!DNL reCAPTCHA] fungerar inte korrekt vid utcheckning, vilket förhindrar att en order placeras.

<u>Steg som ska återskapas</u>:

1. Aktivera valfri typ av [!DNL reCAPTCHA] för presentkort på sidan [!UICONTROL Checkout].
1. Lägg till produkten i kundvagnen och gå till sidan **[!UICONTROL Checkout]**.
1. Expandera presentkortsformuläret och fyll i en giltig presentkortskupong.
1. Klicka på knappen **[!UICONTROL See balance and apply]**.

<u>Förväntade resultat</u>:

Presentkortet har använts.

<u>Faktiska resultat</u>:

Felmeddelandet visas: *[!DNL reCAPTCHA]-valideringen misslyckades, försök igen*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
