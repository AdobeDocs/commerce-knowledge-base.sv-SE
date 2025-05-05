---
title: 'ACSD-48694: Felaktig begärd tillståndsändring förhindrar kunden från att beställa'
description: Använd patchen ACSD-48694 för att åtgärda Adobe Commerce-problemet där felet *Ogiltig tillståndsändring har begärts* förhindrar att en kund beställer.
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694: *Ogiltig lägesändring begärd* fel förhindrar kunden från att beställa

Korrigeringen ACSD-48694 åtgärdar ett problem där felet *Ogiltig tillståndsändring begärd* förhindrar en kund från att göra en beställning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 har installerats. Korrigerings-ID är ACSD-48694. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felet *Ogiltig lägesändring begärd* förhindrar en kund från att göra en beställning.

<u>Steg som ska återskapas</u>:

1. Lägg till en fördröjning under begäran `/estimate-shipping-methods` genom att inkludera en `sleep()` at `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` -funktion, så `/estimate-shipping-methods`-begäran slutförs efter `/shipping-information` när du går från leveranssteg till betalningssteg under utcheckning.
1. Konfigurera sessionen att använda [!DNL Redis] med inställningen *disable_locking:*.
1. Öppna **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** och aktivera *[!UICONTROL Persistent Shopping Cart]*.
1. Logga in som kund och lägg till en produkt i kundvagnen.
1. Låt kundsessionen förfalla. Beständig kaka och vagnen finns kvar.
1. Gå till kassan, lägg till leveransadressen och navigera till betalningsavsnittet.
1. Gå tillbaka till startsidan eller någon annan sida och logga in med kundkontot.
1. Låt sessionen förfalla igen.
1. Gå direkt till kassan och gå till betalningssteget.
1. Försök att lägga ordern.

<u>Förväntade resultat</u>:

* Det finns inget fel.
* Beställningen har placerats och en *Tack*-sida visas.

<u>Faktiska resultat</u>:

Felet *En ogiltig tillståndsändring begärd* visas, men ordningen placeras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
