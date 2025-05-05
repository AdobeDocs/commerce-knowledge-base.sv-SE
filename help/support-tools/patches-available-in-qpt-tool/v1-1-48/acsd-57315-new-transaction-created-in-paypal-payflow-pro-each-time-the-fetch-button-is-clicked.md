---
title: 'ACSD-57315: Ny transaktion skapas i [!DNL PayPal Payflow Pro] varje gång någon klickar på hämtningsknappen'
description: Använd korrigeringsfilen ACSD-57315 för att åtgärda Adobe Commerce-problemet där en ny transaktion skapas i  [!DNL PayPal Payflow Pro] varje gång hämtningsknappen klickas på visningstransaktionsskärmen i [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
exl-id: bcc7467d-09f9-4235-9f9f-46d3034567b8
source-git-commit: d7ace1f20defb01105d4a241f971b06fca052215
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: Ny transaktion skapas i [!DNL PayPal Payflow Pro] varje gång någon klickar på hämtningsknappen

Korrigeringen ACSD-57315 åtgärdar ett problem där en ny transaktion skapas i [!DNL PayPal Payflow Pro] varje gång hämtningsknappen klickas på visningstransaktionsskärmen i [!UICONTROL Admin]. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.48 har installerats. Korrigerings-ID är ACSD-57315. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En ny transaktion skapas i [!DNL PayPal Payflow Pro] varje gång du klickar på hämtningsknappen på skärmen Visa transaktion i [!UICONTROL Admin].

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL PayPal Payflow Pro].
1. Ställ in transaktionsmetoden på *[!UICONTROL Sale]*.
1. Gör en beställning med *kreditkort*.
1. Öppna transaktionen från [!UICONTROL Admin].
1. Klicka på knappen **[!UICONTROL Fetch]**.
1. Kontrollera [!DNL PayPal]-kontot för transaktioner som är relaterade till den placerade ordern.

<u>Förväntade resultat</u>:

Ingen ny betalningstransaktion skapas.

<u>Faktiska resultat</u>:

En ny betalningstransaktion skapas för en order som redan har betalats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
