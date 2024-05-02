---
title: '''ACSD-57315: Ny transaktion skapas i [!DNL PayPal Payflow Pro] varje gång någon klickar på hämtningsknappen'
description: Använd korrigeringsfilen ACSD-57315 för att åtgärda Adobe Commerce-problemet där en ny transaktion skapas i [!DNL PayPal Payflow Pro] varje gång någon klickar på hämtningsknappen på skärmen för visningstransaktion i dialogrutan [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
source-git-commit: b7f85e4fdb7ef4a6328a1a411dac765dd8da083e
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: Ny transaktion skapas i [!DNL PayPal Payflow Pro] varje gång någon klickar på hämtningsknappen

Korrigeringen ACSD-57315 åtgärdar ett problem där en ny transaktion skapas i [!DNL PayPal Payflow Pro] varje gång någon klickar på hämtningsknappen på skärmen för visningstransaktion i dialogrutan [!UICONTROL Admin]. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.48 är installerat. Korrigerings-ID är ACSD-57315. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En ny transaktion skapas i [!DNL PayPal Payflow Pro] varje gång någon klickar på hämtningsknappen på skärmen för visningstransaktion i dialogrutan [!UICONTROL Admin].

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL PayPal Payflow Pro].
1. Ställ in transaktionsmetoden på *[!UICONTROL Sale]*.
1. Beställ med *Kreditkort*.
1. Öppna transaktionen från [!UICONTROL Admin].
1. Klicka på **[!UICONTROL Fetch]** -knappen.
1. Kontrollera [!DNL PayPal] konto för transaktioner relaterade till den placerade ordern.

<u>Förväntade resultat</u>:

Ingen ny betalningstransaktion skapas.

<u>Faktiska resultat</u>:

En ny betalningstransaktion skapas för en order som redan har betalats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
